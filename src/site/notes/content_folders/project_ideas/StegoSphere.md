---
{"dg-publish":true,"permalink":"/content-folders/project-ideas/stego-sphere/","title":"StegoSphere","tags":["others"],"dgShowToc":true}
---


### **1. Project Overview**

**StegoSphere** is a full-featured, responsive web application designed for steganography and data concealment. Built with the **Django web framework**, it provides a secure, user-authenticated platform where users can hide secret text messages within various digital media formats and later extract them.

The application supports a wide range of file types, including images (`.png`), audio (`.wav`), video (`.mp4`), and generic document formats (`.pdf`, `.txt`). To ensure the security of the hidden data, all secret messages are first encrypted using the **AES (Advanced Encryption Standard)** algorithm before being embedded into the cover file.

The project features a modern, interactive user interface with switchable light and dark themes, responsive design for mobile devices, and a complete user history system. It is deployed on the **Render.com** platform, utilizing a PostgreSQL database and an automated deployment pipeline configured via a `render.yaml` file.

---

### **2. System Architecture & Structure**

#### **2.1. Project Folder Structure**

The project is organized into a main Django project directory and two distinct apps, following Django's best practices for modularity.

```
stegasphere/  (The main GitHub repository root)
├── render.yaml
└── steganography_project/  (The Django project root)
    ├── manage.py
    ├── steganography_project/  (Main project configuration)
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── core/  (Django app for user management and general pages)
    │   ├── views.py
    │   ├── urls.py
    │   ├── models.py
    │   └── context_processors.py
    ├── stego/  (Django app for the core steganography functionality)
    │   ├── views.py
    │   ├── urls.py
    │   ├── models.py
    │   ├── forms.py
    │   └── engine.py  (The core steganography algorithms)
    ├── static/  (Project-wide static files)
    │   ├── css/ (dark.css, light.css)
    │   ├── js/ (theme.js, main.js)
    │   └── images/ (favicon.png)
    └── templates/  (Project-wide HTML templates)
        ├── base.html
        ├── core/ (home.html, login.html, signup.html)
        └── stego/ (dashboard.html, history.html)
```

#### **2.2. Technology Stack**

- **Backend:** Python 3.10, Django Framework
    
- **Database:** PostgreSQL (on Render), SQLite3 (for local development)
    
- **Web Server:** Gunicorn (for production)
    
- **Frontend:** HTML5, CSS3, JavaScript
    
- **Deployment:** Render.com, Git, GitHub
    
- **Key Python Libraries:**
    
    - `Pillow`: For image manipulation (LSB steganography).
        
    - `pycryptodome`: For robust AES encryption and decryption.
        
    - `moviepy`: For video processing (extracting and replacing audio tracks).
        
    - `dj-database-url`: For parsing database URLs in production.
        
    - `psycopg2-binary`: PostgreSQL adapter for Python.
        
    - `whitenoise`: For serving static files in a production environment.
        

#### **2.3. Django Application Design (MVT)**

The project follows Django's Model-View-Template (MVT) architecture:

- **Models (`models.py`):** The `StegoHistory` model defines the structure of the database table for storing user activity.
    
- **Views (`views.py`):** These are the Python functions that contain the application's business logic. They process user requests, interact with the database models and the steganography engine, and decide which template to render.
    
- **Templates (`.html` files):** These files define the structure and layout of the user interface. They are rendered by the views with dynamic data.
    

---

### **3. Core Components & Functionality**

#### **3.1. User Authentication (`core` app)**

The application uses Django's built-in authentication system for secure user management.

- **Functionality:** User registration (signup), login, and logout.
    
- **Implementation:** It leverages Django's `UserCreationForm` for signup and `LoginView`/`LogoutView` for authentication, ensuring robust password hashing and session management. Access to the main application dashboard and history is restricted to logged-in users via the `@login_required` decorator.
    

#### **3.2. Database Model (`stego.models.StegoHistory`)**

A single model is used to track all user operations, creating a persistent history for each user.

- **Fields:**
    
    - `user`: A `ForeignKey` linking the record to a specific user.
        
    - `operation_type`: A `CharField` to store whether the operation was "Encode" or "Decode".
        
    - `cover_image`: A `FileField` to store the original file uploaded by the user.
        
    - `stego_image`: A `FileField` to store the output file generated after encoding.
        
    - `secret_message`: A `TextField` to store the message extracted during a decode operation.
        
    - `timestamp`: A `DateTimeField` that automatically records when the operation was performed.
        

#### **3.3. The Steganography Engine (`stego/engine.py`)**

This file contains the heart of the application—the algorithms for data concealment and extraction. All operations follow a two-step process: **Encrypt then Hide**.

**3.3.1. Cryptography Layer (AES)** Before any data is hidden, it is first encrypted to ensure that even if the steganography is detected, the message remains unreadable without the key.

- **Algorithm:** AES (Advanced Encryption Standard) in CBC (Cipher Block Chaining) mode.
    
- **Key Derivation:** The user's provided password (key) is not used directly. Instead, it is passed through the **SHA-256 hashing algorithm** to produce a secure, fixed-length 32-byte key suitable for AES-256.
    
- **Process:** The secret message is padded to be a multiple of the AES block size (16 bytes), encrypted with the derived key, and the Initialization Vector (IV) is prepended to the ciphertext for use during decryption.
    

**3.3.2. Steganography Algorithms** The engine uses different techniques depending on the file type.

- **Images (`.png`): Least Significant Bit (LSB) Substitution**
    
    - **Algorithm:** The encrypted data is converted into a binary string. The algorithm then iterates through the pixels of the image, modifying the least significant bit of each color channel (Red, Green, and Blue) to match one bit from the binary string.
        
    - **Optimization:** To make decoding fast, the **total length of the binary message** is first embedded into the first 32 bits of the image data. The decoder reads this length first, then knows exactly how many more bits it needs to read, avoiding a scan of the entire image.
        
    - **Robustness:** An `ImageOps.exif_transpose()` function from Pillow is used to correct the orientation of images from phones, preventing the output file from being rotated.
        
- **Audio (`.wav`): LSB on Audio Frames**
    
    - **Algorithm:** Similar to images, the audio file is read as a sequence of bytes (frames). The LSB of each byte is modified to hide one bit of the secret message. The message length is also embedded at the beginning for fast extraction.
        
- **Video (`.mp4`): LSB on the Audio Track**
    
    - **Algorithm:** Processing every video frame with LSB is computationally expensive. A more efficient method is used:
        
        1. The `moviepy` library is used to extract the audio track from the video file and save it as a temporary `.wav` file.
            
        2. The existing `hide_data_in_audio` LSB algorithm is run on this temporary audio file.
            
        3. `moviepy` is then used to create a new video file by combining the original video frames with the newly modified (steganographic) audio track.
            
        4. All temporary files are deleted.
            
- **Generic Files (`.pdf`, `.txt`): Data Appending**
    
    - **Algorithm:** For structured formats like PDF, altering internal bytes can easily corrupt the file. A simple and effective method is used:
        
        1. The encrypted secret message is prepended with a unique delimiter (`$$STEGO_END$$`).
            
        2. This entire payload is simply **appended to the end of the original file's byte content**.
            
        3. Most PDF readers and text editors ignore extra data at the end of a file, so the file remains perfectly usable. The decoder simply reads the entire file and looks for the delimiter to find the hidden data.
            

#### **3.4. Views and Workflow (`stego/views.py`)**

The views orchestrate the entire user workflow.

1. A user submits a form on the dashboard (e.g., the encode form).
    
2. The `dashboard_view` receives the request.
    
3. It validates the form data and uploaded file.
    
4. It checks the `content_type` of the file to determine if it's an image, audio, video, etc.
    
5. It calls the appropriate function from the `engine.py` file (e.g., `hide_data` for an image).
    
6. It handles Django's two types of file uploads: for small files kept in memory (`InMemoryUploadedFile`), it first saves them to a temporary file on disk to get a file path.
    
7. The engine returns the processed file. The view saves this file and creates a new `StegoHistory` record in the database.
    
8. Finally, it redirects the user to their history page with a success message.
    

---

### **4. User Interface & Experience (UI/UX)**

- **Theming:** The application features switchable light and dark themes, implemented using CSS variables. A JavaScript function toggles a class on the body and swaps the stylesheet link, saving the user's preference in the browser's `localStorage`.
    
- **Responsiveness:** A "hamburger" menu is implemented for mobile devices using a CSS media query and JavaScript. On screens narrower than 768px, the horizontal navigation collapses into a vertical, togglable menu.
    
- **Interactivity:**
    
    - **Drag-and-Drop:** File input fields are enhanced with JavaScript to allow users to drag and drop files directly into a drop zone, providing visual feedback.
        
    - **Dynamic UI:** JavaScript is used to display selected filenames, toggle the visibility of decoded messages on the history page, and manage the database expiration countdown timer.
        

---

### **5. Deployment & DevOps**

The application is configured for production deployment on the Render.com cloud platform.

- **Infrastructure as Code (`render.yaml`):** The entire deployment is defined in a `render.yaml` file. This "blueprint" tells Render how to build and run the application, ensuring consistent and reproducible deployments. It defines:
    
    - A free-tier **PostgreSQL database service**.
        
    - A free-tier **Web Service** running Python 3.10.
        
    - The **Root Directory** of the Django project.
        
    - The **Build Command** to install dependencies (`pip install`), collect static files (`collectstatic`), and run database migrations (`migrate`).
        
    - The **Start Command** to run the Gunicorn production server.
        
    - A **Buildpack** to install the `ffmpeg` system dependency required by `moviepy`.
        
    - **Environment Variables** for the `SECRET_KEY` and the `DATABASE_URL`, linking the web service to the database.
        
- **Static File Handling:** In production (`DEBUG=False`), Django does not serve static files. **WhiteNoise** is used as a middleware to allow the Gunicorn server to efficiently serve compressed static files (CSS, JS, images).
    
- **Automated Admin Creation:** Since Render's free tier does not provide shell access to run `createsuperuser`, a custom **Django data migration** was created. This script runs automatically during deployment, checks if a superuser exists, and if not, creates one using credentials securely stored in environment variables on Render.
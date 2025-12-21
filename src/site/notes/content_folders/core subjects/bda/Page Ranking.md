---
{"dg-publish":true,"permalink":"/content-folders/core-subjects/bda/page-ranking/","dgShowToc":true}
---

## 1. What is Page Ranking?

**Page Ranking** is a technique used to **measure the importance (authority) of a web page** by analyzing how pages are **linked to each other** on the web.

### Fundamental idea

> A page is important if **many pages link to it**,  
> and it is **even more important if those linking pages are themselves important**.

This means:

- Importance is **not local**
    
- Importance is **inherited**
    
- Importance is **relative**, not absolute

---

## 2. Modeling the Web as a Graph

To reason about importance mathematically, the web is modeled as a **directed graph**.

- **Nodes (vertices)** → web pages
    
- **Directed edges** → hyperlinks


If page `u` links to page `v`, we write:

```
u → v
```

### Why this model is used

- Graphs allow us to analyze **connections**
    
- Importance can be treated as something that **flows through edges**
    
- Many ranking algorithms operate naturally on graphs


---

## 3. In-Degree and Out-Degree (Initial Intuition)

### In-degree (Visibility)

- Number of incoming links to a page
    
- Indicates how many pages recommend it


### Out-degree (Luminosity)

- Number of outgoing links from a page
    
- Indicates how widely a page spreads its influence


### Early ranking idea

Pages with:

- High in-degree
    
- Low out-degree


were assumed to be more authoritative.

---

## 4. Why Simple In-Degree Fails

The PDF explicitly points out a major flaw:

> **All links are not equally important.**

### Problem example

- A link from Google’s homepage
    
- A link from an unknown personal blog


Both increase in-degree by 1, but **clearly they should not contribute equally**.

### Conclusion

Simple link counting:

- Ignores link quality
    
- Ignores source importance
    
- Produces misleading rankings


This leads to the **parent-based approach**.

---

## 5. Parent Pages and Child Pages

For any page ( v ):

- **Parent pages** → pages that link to ( v )
    
- **Child pages** → pages that ( v ) links to


If:

```
u → v
```

then:

- ( u ) is a **parent** of ( v )
    
- ( v ) is a **child** of ( u )


This distinction is crucial because **PageRank is computed using parent pages only**.

---

## 6. Core Insight: Authority Comes from Parents

This is the **most important conceptual step in the PDF**:

> **The importance of a page depends on the importance of its parent pages.**

Meaning:

- A page is not important by itself
    
- It becomes important **because important pages point to it**


This creates a **recursive definition**:

- Importance depends on importance


---

## 7. Authority Flow Concept (How Ranking Works)

The PDF explains PageRank using an **authority flow analogy**:

- Each page has some authority (rank)
    
- When a page links to others, it **passes authority forward**
    
- Authority is **shared among all outgoing links**


### Why sharing is necessary

If a page links to many pages:

- It should not give **full authority to all**
    
- Its authority must be **divided**


This idea leads directly to **division by out-degree** in formulas.

---

## 8. Dead Ends (Dangling Pages)

### What are dead ends?

Pages that:

- Have **no outgoing links**
    
- Only receive links


Examples:

- PDF files
    
- Standalone articles
    
- Final content pages


---

### Why dead ends are a problem

- Authority flows **into** them
    
- Authority does **not flow out**
    
- This causes **rank sinks**


Over time:

- Authority accumulates and gets stuck
    
- Rankings become unstable


This problem motivates later improvements.

---

## 9. Other Web Graph Metrics (Context)

Before PageRank, other metrics were studied.

### Closeness Centrality

C(u)=1∑vd(u,v)C(u) = \frac{1}{\sum_{v} d(u,v)}

#### Why this formula exists

- Pages closer (in hops) to many others are more central
    
- Inverse is used so:
    
    - Smaller distance → higher score


#### Limitation

- Ignores link direction
    
- Ignores authority quality
    
- Not suitable alone for web ranking


---

## 10. Basic PageRank (In-Degree Based)

The first PageRank formulation formalizes authority flow:

$$ PR(v)=c∑u→vPR(u)N(u)PR(v) = c \sum_{u \rightarrow v} \frac{PR(u)}{N(u)} $$

### Conceptual derivation

- Each parent page ( u ) has authority ( PR(u) )
    
- That authority is divided among its ( N(u) ) outgoing links
    
- Page ( v ) collects contributions from **all parents**
    
- ( c ) ensures normalization


This matches the **authority flow model exactly**.

---

## 11. PageRank Using Parent Authority (Generalized Form)

The PDF then generalizes the idea:

$$ R(v)=∑u∈PA(v)R(u)⋅w(u,v)R(v) = \sum_{u \in PA(v)} R(u) \cdot w(u,v) $$

### Why this is introduced

- Not all links are equally important
    
- Some links may:
    
    - Be stronger
        
    - Be topic-relevant
        
    - Carry more trust


The weight ( w(u,v) ) allows:

- Flexible influence modeling
    
- More realistic ranking


---

## 12. Random Surfer Model (Damping Factor)

### Problem addressed

- Dead ends
    
- Rank sinks
    
- Infinite loops
   

### Assumption

A user:

- Follows links randomly
    
- Occasionally jumps to a random page


---

### PageRank with Damping Factor

$$ R(v)=(1−α)∑u∈PA(v)R(u)∣out(u)∣+αE(v)R(v) = (1 - \alpha) \sum_{u \in PA(v)} \frac{R(u)}{|out(u)|} + \alpha E(v) $$

### Why this works

- ( (1-\alpha) ) → link following
    
- ( \alpha ) → random jump
    
- Prevents authority from getting trapped
    
- Guarantees convergence


Typical value:

```
\alpha = 0.15
```

---

## 13. Iterative Computation of PageRank

PageRank cannot be solved directly.

### Method

1. Initialize all pages equally
    
2. Recompute ranks using the formula
    
3. Repeat until stable


### Convergence condition

$$ ∣R(k+1)(v)−R(k)(v)∣<ϵ|R^{(k+1)}(v) - R^{(k)}(v)| < \epsilon $$

This ensures:

- Stability
    
- Termination
    
- Reliable ranking


---

## 14. PageRank at Scale

Because the web is massive:

- PageRank is computed using **distributed systems**
    
- Iterative nature fits:
    
    - MapReduce
        
    - Spark
    
- Each iteration is parallelizable


---

## 15. Static vs Dynamic PageRank

### Static PageRank

- Fixed number of iterations
    
- Faster
    
- Less accurate
   
### Dynamic PageRank

- Runs until convergence
    
- More accurate
    
- Preferred in practice


---

## 16. Topic-Sensitive PageRank

### Motivation

A page may be important **only for a topic**.

### Topic-Sensitive Formula

$$ R(v)=(1−αt)∑u∈PA(v)R(u)∣out(u)∣+αtEt(v)R(v) = (1 - \alpha_t) \sum_{u \in PA(v)} \frac{R(u)}{|out(u)|} + \alpha_t E_t(v) $$

### Why this helps

- Biases ranking toward topic pages
    
- Produces topic-specific importance scores
    
- Improves search relevance


---

## 17. Link Spam and Spam Mass

### Link spam

Artificial inflation of rank by:

- Creating fake pages
    
- Pointing them to a target page


### Observation

Natural web graphs follow predictable patterns  
Spam graphs do not.

This motivates spam-aware ranking methods.

---

## 18. HITS Algorithm (Hubs and Authorities)

### Authority score

$$ A(p)=∑q→pH(q)A(p) = \sum_{q \rightarrow p} H(q) $$

### Hub score

$$ H(p)=∑p→qA(q)H(p) = \sum_{p \rightarrow q} A(q) $$

### Interpretation

- Good hubs point to good authorities
    
- Good authorities are pointed to by good hubs
    
- Mutual reinforcement


---

## 19. PageRank vs HITS (Exam Favorite)

|Aspect|PageRank|HITS|
|---|---|---|
|Scope|Global|Query-specific|
|Output|Single rank|Hub + Authority|
|Dead ends|Handled|Not handled|
|Stability|High|Lower|

---

## 20. Limitations of Page Ranking

- Topic drift
    
- Link manipulation
    
- Freshness bias
    
- Structural bias
    
- Computational cost


These motivate hybrid ranking models.

---

## Final Exam Memory Lock

> **PageRank is authority propagation over a directed graph with random escape.**

---
## Mental Model

- PageRank measures **global importance**
    
- Importance flows through links
    
- Links from important pages matter more
    
- Random jumps prevent rank sinks
    
- Iterative computation ensures stability
    
- Extensions handle topics and spam

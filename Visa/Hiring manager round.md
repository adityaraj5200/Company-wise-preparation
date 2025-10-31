# Tip: This round is of 1 hour so they will grill on technical questions. Make sure all the things I have mentioned in resume I revise them real quick and get common questions and answers from chatGPT around them.

### Based on resume: 


Based on youtube video (https://www.youtube.com/watch?v=pq_ZqWqsSHs):
### Projects.
* What problems did I faced?
* He then asked me what I could have done to improve this project.

### SQL vs NoSQL
SQL (Relational Databases): These databases use a relational model, organizing data into tables with predefined schemas. Data is structured into rows and columns, and relationships between tables are established using foreign keys. This ensures data integrity and consistency.
NoSQL (Non-Relational Databases): NoSQL databases employ various data models, including key-value stores, document stores, wide-column stores, and graph databases. They are designed for handling unstructured or semi-structured data and do not enforce a fixed schema.


### How hashMap internally works

### Why do you want to join visa.
I want to join Visa because it’s a company that has demonstrated long-term stability and consistent growth over the years. Visa has been a leader in the payments industry for decades, continuously evolving its technology to stay ahead of the market. The fact that Visa’s business and stock performance have remained strong and steadily rising reflects how well the company adapts to change and maintains trust globally.

From a career perspective, I’m looking for a company that’s both technically strong and stable, where I can build impactful systems at scale and grow in the long term — and Visa clearly provides that environment.

### What difficulty you faced while doing the projects.


### what is the difference between semaphore and mutex.
A mutex is a locking mechanism that allows only one thread to access a resource at a time, ensuring mutual exclusion, while a semaphore is a signaling mechanism that controls access to a finite number of resources using a counter (signaling system). A key difference is that mutexes have "ownership," meaning the same thread that locks a resource must unlock it, whereas a semaphore's value can be signaled by any process, making it suitable for signalling between threads. 

### different network topologies and their respective advantages and disadvantages.
1. **Bus Topology**
   - Advantages: Simple, easy to implement, requires less cabling.
   - Disadvantages: Difficult to troubleshoot, limited scalability, single point of failure.

2. **Star Topology**
   - Advantages: Easy to manage, isolate failures, scalable.
   - Disadvantages: Central hub failure affects entire network, more cabling needed.

3. **Ring Topology**
   - Advantages: Data flows in one direction, predictable performance, easy fault isolation with dual rings.
   - Disadvantages: Single node failure can disrupt network (unless dual ring), harder to install.

4. **Mesh Topology**
   - Advantages: High redundancy and reliability, fault tolerant, dedicated links improve performance.
   - Disadvantages: Expensive due to cabling, complex setup and maintenance.

5. **Tree Topology**
   - Advantages: Hierarchical, scalable, easy to manage large networks.
   - Disadvantages: Root node failure can affect entire branch, more cabling than bus.

6. **Hybrid Topology**
   - Advantages: Combines strengths of multiple topologies, flexible and scalable.
   - Disadvantages: Complex design and maintenance, expensive to implement.


### SQL questions followed, covering topics like primary keys and foreign keys, which are fundamental to database management.

### SpringBoot features:
* Auto-Configuration
* Starter Dependencies
* Opinionated Defaults


### Even a few questions on OOPS were asked like Polymorphism and encapsulation.
### We discussed the latest technology trends that had fascinated me and explored potential improvements in those areas.
### Design a new Cryptographic Algorithm.
### Can a structure point to itself?
Yes, it can.
```cpp
struct Node {
    int data;
    struct Node* next; // pointer to another Node (can be itself)
};
```

### Which is better, an array of pointers or a 2-D Array?
Rule of thumb:
* Use 2-D array if dimensions are fixed and performance is critical.
* Use array of pointers if row sizes vary or dynamic allocation is needed.

### Difference between Memset and Memcopy.
Here’s a concise comparison of `memset` and `memcpy`:

```
1. **memset**
   - Purpose: Fill a block of memory with a single byte value.
   - Prototype: void *memset(void *ptr, int value, size_t num);
   - Usage: Initialize arrays, zero-out buffers.
   - Example: memset(arr, 0, sizeof(arr));
   - Key Point: Sets memory to **one repeated byte**; not for copying data.

2. **memcpy**
   - Purpose: Copy a block of memory from a source to a destination.
   - Prototype: void *memcpy(void *dest, const void *src, size_t num);
   - Usage: Copy arrays, structs, or buffers.
   - Example: memcpy(dest, src, sizeof(src));
   - Key Point: Copies **exact bytes** from source to destination; cannot overlap memory safely.
```

**Summary:**

* `memset` → initialize/fill memory.
* `memcpy` → copy memory.


### If you join VISA then what will I want to change about or add to its present system/infrastructure?
* Enhance automation and observability
* Strengthen security


### How will Trump's visit be beneficial for India.
### Questions around microservices.
### How do you handle conflict in a team.
I handle team conflicts by focusing on facts and open communication. First, I listen to each person’s perspective to understand the root cause. Then I encourage a data-driven discussion, weighing pros and cons rather than opinions. I aim to find a compromise or solution that balances technical correctness, business needs, and team consensus. If needed, I involve stakeholders to align on priorities. The key is to stay professional, respectful, and solution-focused, ensuring the conflict leads to a better outcome rather than friction.

### Describe a time you faced a conflict in a team and how you handled it.
Situation: While working on a security certification project at Amazon, two team members disagreed on the approach to fix a potential XSS vulnerability — one preferred a quick patch to meet deadlines, the other insisted on a full code refactor for long-term safety.

Task: As the responsible engineer, I needed to resolve the conflict while ensuring both security and timely delivery.

Action: I organized a short discussion where each presented their approach and risks. I suggested a hybrid solution: implement the quick patch to address the immediate vulnerability, while scheduling a refactor in the next sprint for long-term robustness. I also documented the plan and communicated it with the team and stakeholders.

Result: The vulnerability was fixed without delaying the project, both team members felt heard, and the refactor later improved code maintainability. This approach strengthened team collaboration and trust for future security tasks.

### Why do you want to work at Visa?

### How do you manage deadlines for multiple projects?
I manage multiple project deadlines by prioritizing tasks based on impact and urgency. I break each project into smaller milestones, set realistic timelines, and use tools like Jira or spreadsheets to track progress. I also schedule regular check-ins to identify blockers early and adjust priorities if needed. Clear communication with stakeholders ensures expectations are aligned, helping me deliver quality work on time without overloading myself.

### What would you do if a teammate was not contributing?
If a teammate is not contributing, I first try to understand the reason—it could be lack of clarity, skill gaps, or personal issues. I offer support by clarifying expectations, providing guidance, or redistributing tasks if needed. If the issue persists, I escalate it to the lead or manager with a focus on finding a solution rather than assigning blame, ensuring the team meets its goals while maintaining a collaborative environment.

### What if a colleage is taking credit of your work?
If a colleague is taking credit for my work, I would first address it privately with them to clarify contributions and understand their perspective. If the issue continues, I would document my work clearly and communicate progress and outcomes to the manager or team in a factual, professional way. My focus would be on resolving the situation respectfully while ensuring the team and project stay on track.






HR-based questions :

* What are your strengths and weakness?
* Tell me a situation in which you are in stressed and what you did to a comeback. Then he was quite happy with my performance.
* What will you do in a situation where your colleague is taking credit of the work done by you?
* Where do you see yourself in 5 years?
* Why do you want to join visa?
* Tell me a good thing and a bad thing manager would say about you?
* Will AI replace humans?
* How would you want me to introduce you to my team? Like what is your best skillset

---

* How will I create a doubly-linked list? A real life use of doubly-linked list?
* What to do if there are too many requests to a web server? Don’t know if they’re correct. I feel it was a more test to see your critical thinking and acquired knowledge.
* What do you want to work in?
* Why do you want to join VISA?
* Asked what kept them at VISA? And what they’re objectives in their career?






---

* Tell me something about your projects?
* Difference between SQL and NO-SQL Database?
* Real life examples where we will prefer using SQL and NO-SQL Database?
Here’s a concise, interview-ready answer with real-life examples:

---

**SQL Database (Relational):**

* **Use case:** Structured data with complex relationships and strong consistency requirements.
* **Example:** Banking transactions, e-commerce orders, or employee payroll systems where **ACID compliance** and **joins across tables** are essential.

**NoSQL Database (Non-relational):**

* **Use case:** Unstructured or semi-structured data, high scalability, flexible schema, or high read/write throughput.
* **Example:** Social media feeds, product catalogs, IoT sensor data, or real-time analytics where **schema changes are frequent** and horizontal scaling is required.

**Rule of thumb:** Use SQL for **structured, consistent data**, and NoSQL for **flexible, scalable, high-throughput applications**.

* How will you handle 1 million requests on your application?
Here’s a structured, interview-ready answer:

---

To handle **1 million requests**, I would focus on **scalability, performance, and reliability**:

1. **Load Balancing:** Distribute requests across multiple server instances to prevent overload.
2. **Caching:** Use **CDNs or in-memory caches** (e.g., Redis) for frequently requested data to reduce database hits.
3. **Database Optimization:** Implement **read replicas, sharding, or indexing** to handle high database load efficiently.
4. **Asynchronous Processing:** Use **queues or message brokers** (e.g., SQS, Kafka) for non-critical or delayed tasks.
5. **Auto-scaling:** Dynamically add server resources in cloud environments to meet traffic spikes.
6. **Monitoring and Alerts:** Track **latency, error rates, and throughput** to detect bottlenecks quickly.


* Difference between http and https?
Here’s a concise, interview-ready answer:

---

**HTTP (HyperText Transfer Protocol):**

* Protocol for transferring data between client and server.
* **Not encrypted**, so data (like passwords) can be intercepted.
* Default port: **80**.

**HTTPS (HTTP Secure):**

* HTTP over **TLS/SSL**, meaning communication is **encrypted**.
* Ensures **confidentiality, integrity, and authentication**.
* Default port: **443**.

**Summary:** HTTPS is a **secure version of HTTP**, protecting data from eavesdropping and tampering.

---

I can also make a **2–3 sentence spoken version** suitable for verbal delivery if you want.

## What are web sockets?
WebSockets are a protocol that enables full-duplex, bidirectional communication between a client (like a browser) and a server over a single TCP connection. Unlike HTTP, which is request-response based, WebSockets allow the server to push data to the client in real time without the client repeatedly polling.

Use cases: live chats, online gaming, stock tickers, collaborative editing, or real-time notifications.

## Software Development Methodologies?
## Software Development Life Cycle?
Here’s a concise, interview-ready explanation of the **Software Development Life Cycle (SDLC):**

---

**SDLC** is a structured process used to design, develop, test, and deploy software efficiently and with high quality.

**Key Phases:**

1. **Requirement Analysis:** Gather and document functional and non-functional requirements.
2. **System Design:** Plan architecture, database, and technology stack.
3. **Implementation / Coding:** Developers write code according to design specifications.
4. **Testing:** Verify functionality, performance, and security; fix defects.
5. **Deployment:** Release the software to production.
6. **Maintenance:** Monitor, update, and enhance software post-deployment.


## Which is more important development or testing and why?
Both development and testing are equally important because they serve complementary purposes. Development builds the functionality, while testing ensures correctness, reliability, and quality. Without proper development, there’s no product; without proper testing, the product may fail in production, causing bugs, security issues, or user dissatisfaction. Ideally, they should work hand-in-hand, with testing integrated throughout the development process (e.g., unit tests, integration tests, automated CI/CD pipelines) to deliver a robust product.

## What are Deadlocks?
Deadlock occurs in a system when two or more processes are waiting indefinitely for resources held by each other, so none of them can proceed.

## Necessary conditions for deadlock? Given a printer and a scanner when can deadlock occur?
Necessary conditions for deadlock:
* Mutual Exclusion: Resources cannot be shared simultaneously.
* Hold and Wait: Processes hold resources while waiting for others.
* No Preemption: Resources cannot be forcibly taken away.
* Circular Wait: A cycle of processes exists where each waits for the next.

Handling deadlocks: Avoidance, prevention, detection, or recovery (e.g., killing a process, rolling back, or resource preemption).

## Deadlock handling techniques? Which technique is used by windows OS?

## Process vs thread?


## How to best maintain a sorted list from a stream of integers?



--- 

# From chatGPT:

In a **hiring manager (HM) round** for a software engineer position at a company like Visa, the focus shifts from purely technical assessment to a broader evaluation of your fit for the team, role, and organization. Here’s a concise breakdown:

### **Common Question Categories**

1. **Behavioral / STAR-based**

   * Tell me about a time you faced a technical challenge and how you solved it.
   * Describe a situation where you disagreed with a team member or manager.
   * How do you prioritize tasks under tight deadlines?
   * Times you showed leadership or ownership.

2. **Project / experience discussion**

   * Walk me through your most recent project.
   * What was your contribution, trade-offs you made, technologies used.
   * Challenges and lessons learned.

3. **Technical discussion (high-level)**

   * Explain system design decisions in your project.
   * How would you scale a service? (can be architecture/design focused)
   * Questions on algorithms/data structures may come up, but usually discussion-based, not coding live.

4. **Behavioral / culture fit**

   * How do you handle feedback?
   * How do you learn new technologies?
   * Examples of teamwork or conflict resolution.

5. **Career & motivation**

   * Why Visa?
   * What excites you about this role?
   * Where do you see yourself in 2–3 years?

---

### **Tips**

* Use **STAR method** for behavioral questions.
* Prepare **2–3 projects** in depth.
* Be ready to **explain trade-offs** and decisions.
* Show curiosity about the role and company.

---

If you want, I can draft a **list of 15–20 highly likely HM round questions for a Visa SDE** that you can prep answers for. It’ll save a lot of time. Do you want me to do that?

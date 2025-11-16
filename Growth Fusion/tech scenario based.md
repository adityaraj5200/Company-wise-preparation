# Q.1: How would you integrate with a third-party API that has rate limits?
**Copy-pastable interview-style answer (crisp, to the point):**

**Answer:**
To integrate with a third-party API that enforces rate limits, I would design the client so that it **never exceeds the allowed request quota**, while still maximizing throughput. I would follow these steps:

1. **Read API’s rate-limit contract** (e.g., X requests/minute or per access token).
2. **Add a client-side rate limiter** — e.g., **Token Bucket** or **Leaky Bucket** — to throttle outgoing requests before they hit the third-party.
3. **Implement exponential backoff + retries** for 429 responses (Too Many Requests).
4. **Use queuing**: enqueue incoming tasks and let a worker process them at a safe rate.
5. **Cache responses** whenever possible to reduce unnecessary calls.
6. **Use batching** if the API supports it.
7. **Log and monitor rate-limit usage** to detect approaching thresholds.

---

### Example architecture (interviewer-ready)

* Your service receives work (e.g., fetch campaign performance).
* Work goes into a **queue**.
* A controlled number of workers pull tasks from the queue.
* A **rate-limiter** ensures workers never exceed X requests per second/minute.
* On failure **429**, worker waits (Retry-After header) and retries.

---

### Example Java code (simple Token Bucket)

```java
public class RateLimiter {
    private long lastRefillTime;
    private double tokens;
    private final double capacity;
    private final double refillRatePerSec;

    public RateLimiter(double capacity,double refillRatePerSec){
        this.capacity=capacity;
        this.refillRatePerSec=refillRatePerSec;
        this.tokens=capacity;
        this.lastRefillTime=System.nanoTime();
    }

    public synchronized boolean allowRequest(){
        refill();
        if(tokens>=1){
            tokens-=1;
            return true;
        }
        return false;
    }

    private void refill(){
        long now=System.nanoTime();
        double seconds=(now-lastRefillTime)/1e9;
        tokens=Math.min(capacity,tokens+seconds*refillRatePerSec);
        lastRefillTime=now;
    }
}
```

Usage:

```java
RateLimiter rl=new RateLimiter(100,100); // 100 requests/sec

if(rl.allowRequest()){
    callThirdPartyApi();
} else {
    queueForLater();
}
```


# Q.2: How would you retry failed API calls without duplicating actions?
**Copy-pastable, interviewer-style answer:**

**Answer:**
I avoid duplicating actions during retries by making every API call **idempotent** and by assigning each operation a **unique request identifier** so the server can detect duplicates.

---

### 1. **Use Idempotency Keys**

* Client generates a unique `idempotency_key` for each logical operation.
* Key is sent with every retry.
* Server stores the result for that key and returns the same response if the request repeats.

This guarantees that **retrying does not repeat the action** (e.g., creating an order, updating a budget, triggering a campaign change).

---

### 2. **Idempotent API Design**

* Use **PUT** for updates (`PUT /campaign/123/budget`), not POST.
* Ensure repeated calls produce the same end state.
* Avoid “increment” and “decrement” operations; instead send **absolute values**.

---

### 3. **Safe Retry Strategy**

* Retry only on **safe failure conditions** (network timeout, 429, 5xx).
* Exponential backoff + jitter.
* Respect `Retry-After` header when rate-limited.

---

### 4. **Server-Side Duplicate Detection**

* Server keeps a small cache or persistent store:
  `{idempotency_key → result + status}`
* When the same key arrives again:

  * Do not execute the action
  * Return the stored response

---

### 5. **Client Logic Flow**

```
1. Generate idempotency_key
2. Send request with the key
3. If timeout or 5xx → retry with same key
4. Server returns either:
   - Fresh result (first execution)
   - Cached result (duplicate request)
```

---

### Short Example (Java Pseudocode)

```java
String key=UUID.randomUUID().toString();

HttpRequest req=HttpRequest.newBuilder()
    .uri(apiUrl)
    .header("Idempotency-Key",key)
    .build();

for(int i=0;i<MAX_RETRIES;i++){
    HttpResponse res=client.send(req);

    if(isSuccess(res)) return res;
    if(isRetryable(res)) Thread.sleep(backoff(i));
}

throw new RuntimeException("Failed after retries");
```


# Q.3: How do you ensure idempotency in API integrations?wer-style answer:**

**Answer:**
I ensure idempotency in API integrations by designing every operation so that **repeated requests produce the same final result**, regardless of how many times they run. I enforce this through a combination of **client-side guarantees**, **server-side guarantees**, and **API design choices**.

---

## 1. Idempotency Keys (Most Important)

* Client generates a unique `idempotency_key` per logical operation.
* Every retry includes the same key.
* Server stores `{idempotency_key → final_result}`.
* If a duplicate request arrives, server returns the stored result instead of re-running the action.

This completely prevents duplicates in retries.

---

## 2. Idempotent HTTP Methods

* Use **PUT** or **DELETE** instead of POST whenever possible.
* PUT “sets a value” → can be repeated safely.
* POST “creates something” → not inherently idempotent unless combined with an idempotency key.

---

## 3. Absolute Updates Instead of Relative Updates

Avoid:

* `incrementBudget(+50)`
* `addSpending(20)`

Prefer:

* `setBudget(500)`
* `setDailySpend(120)`

Repeated calls won’t cause double increments.

---

## 4. Server-Side Deduplication

When an idempotency key is received:

* If **first time** → perform the action and store the result.
* If **repeated** → skip execution, return saved response.

Used for payment APIs, campaign creation, order processing, and ad creatives.

---

## 5. Retry Strategy Only on Safe Errors

* Retry for: timeouts, network failures, HTTP 429, 500-series.
* Do **not** retry blindly on 400 errors.
* Always include the same idempotency key per operation.

---

## 6. Database-Level Protection

For critical operations:

* Use unique constraints (e.g., unique creative_id, order_id).
* Use UPSERT semantics (`INSERT ON CONFLICT DO NOTHING`).

# Q.4: How would you design a pipeline that pulls campaign metrics every hour?


# Q.4: 
# Q.4: 


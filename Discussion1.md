# 1

An autonomous vehicle demonstrates the full AI perception, reasoning, action feedback loop by continuously sensing its environment, interpreting what it sees, deciding what to do, acting on that decision, and then checking the results in real time. In the perception stage, it uses cameras, LiDAR, radar, GPS, IMU, and sensor fusion to detect lanes, traffic signs, pedestrians, vehicles, and obstacles while also localizing itself on a map. In the reasoning stage, it predicts the behavior of other road users, follows traffic rules, assesses risks, and plans safe routes and paths. In the action stage, the system sends commands to steering, braking, throttle, and other actuators to physically control the vehicle. Finally, in the feedback stage, it monitors speed, position, sensor data, and vehicle movement to correct errors, respond to changing conditions, and maintain safety.

# 2

### (a)
```
function fib(n):
    if n <= 1: return n # O(1)
    return fib(n-1) + fib(n-2) # T(n - 1) + T(n - 2)
```

For the naive recursive Fibonacci algorithm, each call to `fib(n)` creates two additional recursive calls: `fib(n-1)` and `fib(n-2)`. This creates a large recursion tree with many repeated calculations. For example, `fib(5)` computes `fib(4)` and `fib(3)`, but `fib(4)` also computes `fib(3)` again. Because the same Fibonacci values are recomputed many times, the time complexity is exponential. More specifically, the recurrence is:

$$T(n) = T(n-1) + T(n-2) + O(1)$$

This gives a time complexity of approximately $O(2^n)$. Or more tightly, $O(\phi^n)$ where $\phi \approx 1.618$ is the golden ratio. The space complexity is $O(n)$ because the deepest chain of recursive calls goes from `fib(n)` down to `fib(0)` or `fib(1)`, giving a maximum recursion depth of $n$.

### (b)
```
function fibDP(n):
    if n <= 1: return n # O(1)
    
    F = [-1] * (n + 1) # O(n)
    F[0] = 0 # O(1)
    F[1] = 1 # O(1)

    for i = 2 to n: # O(n)
        F[i] = F[i-1] + F[i-2] # O(1)
    
    return F[n]
```

The dynamic programming version avoids repeated work by storing previous Fibonacci values in an array. Each Fibonacci number from `F[0]` to `F[n]` is computed exactly once. The loop runs from $2$ to $n$, so the time complexity is $O(n)$. The space complexity is $O(n)$ because the algorithm stores all Fibonacci values in the array `F`. This could be optimized further to $O(1)$ if only the previous two values were stored instead of the entire array.

### Comparison

When $n$ is large, say $n = 40$, the difference between the two algorithms is very large. The naive recursive version makes an exponential number of function calls. In fact, computing `fib(40)` recursively results in hundreds of millions of function calls because the same smaller Fibonacci values are recalculated over and over. This would take noticeably longer and could cause the program to time out, resulting in a very slow end-user experience. Its memory use is not huge at one time because it only stores the current recursion stack, but the stack depth can still reach about 40 calls.

In contrast, the dynamic programming version only computes each Fibonacci value once. For $n = 40$, it only fills in values from `F[0]` through `F[40]`. This runs almost instantly. Its memory use is also small, requiring an array of only $n + 1 = 41$ values. Overall, the dynamic programming algorithm is much more efficient because it changes the problem from exponential time to linear time.

# 3

**(a)** Task B will be removed first because it has priority 1, which is the lowest number and therefore the highest priority.

**(b)** Task D will be removed second because after B is removed, D has the next highest priority with priority 2.

**(c)** No, this is not the same order as a regular FIFO queue. A FIFO queue removes items in the order they were inserted, so it would remove A first. A priority queue instead removes the item with the highest priority first, which in this case means the lowest priority number.

**(d)** If a new task E with priority 0 is added, task E should be removed next because priority 0 is the highest priority among all tasks.

**(e)** A priority queue is different from a regular queue because items are removed based on their priority, not based only on insertion order. In a regular FIFO queue, the first item inserted is the first item removed.

# 4

For this AI customer support classifier, the team should consider the trade-off between time and accuracy. A deeper or more complex model may classify messages more accurately, but it also takes longer to run. This matters when the system is processing thousands of messages per hour, since slow response times could result in a frustrating end-user experience. They also need to consider latency versus throughput. In the modern world, where customers often live chat with agents, low latency is important for a seamless user experience. However, this can come with the trade-off of less efficient processing. If the system processes large groups of messages at once, batching may improve efficiency and throughput.

The most important trade-off for this system is probably latency versus throughput because the system must handle a large volume of messages while still responding quickly. If the system focuses only on batching for throughput, individual users may experience delays. But if it focuses only on low latency, it may not scale efficiently. Accuracy is also important, but the system needs to balance fast responses with high-volume processing to work well in production.

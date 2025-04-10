---
layout: post
title: SIEVE a drop-in eviction algorithm that’s simpler than LRU
subtitle: Your cache is silently draining your budget
tags: [caching,performance,eviction]
---

Your cache is silently draining your budget. Could 20 lines of code fix that?

Meet SIEVE – a drop-in eviction algorithm that’s simpler than LRU and more efficient than ARC, TwoQ, and even ML-based policies.

### Why care?
- Up to 63% lower miss ratio than ARC
- 2× higher throughput in multi-threaded workloads
- Zero locks on cache hits = massive scalability boost
- Implementation in <20 lines of code
- No tuning. No parameters. No drama.


### 💰 What does that mean in dollars?
Let’s say your backend cache serves 50 million requests per hour and you’re spending $0.10 per GB-hour of memory + $0.02 per 1M backend requests due to cache misses.
Switching from ARC to SIEVE can cut miss ratio by up to 63% – meaning fewer trips to the backend, less memory pressure, and better CPU efficiency.
Even a 10% miss reduction can save tens of thousands of dollars per month at scale. And it costs almost nothing to try.
SIEVE has been tested on 1,559 real-world traces (together contain 247,017 million requests to 14,852 million objects) from Twitter, Meta, and large CDNs — and consistently beats state-of-the-art algorithms in both efficiency and simplicity.
It doesn't just outperform LRU. It redefines what a cache eviction algorithm can be: elegant, fast, and production-ready.

### Where can it help?
- CDN edge caches
- Internal KV stores
- Redis-like in-memory systems
- Any place you're still relying on LRU as the default

### What's the magic?
SIEVE avoids LRU's eager promotion and complex structures. Instead, it uses a clever combination of lazy promotion and quick demotion.
Its internal logic is simple:
- A FIFO queue
- A moving "hand" pointer
- A 1-bit visited flag per object

No multiple queues. No ML. No guesswork. And yet, it outperforms 9 state-of-the-art algorithms on 45%+ of traces.
And because it's lock-free on hits, it scales beautifully with modern CPUs.

### Bottom line
If you're still using LRU, ask yourself: Is it because it's the best choice — or just the default one?
Swap in SIEVE. Save compute. Save money.

Read more https://lnkd.in/eWQieNsf

My implementation https://github.com/patriksima/SieveCache
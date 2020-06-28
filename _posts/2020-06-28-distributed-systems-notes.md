---
layout: default
title: Distrubuted Systems Notes
dates: 2020-06-28 14:30 IST
comments: true
---
#Distributed Systems

##Definition:
Multiple computers working on a single goal, presenting an abstraction of being a single unit to the user

##Characteristics
- Computers/nodes operate concurrently
- Computers/nodes fail independently
- Asynchronous – Do not share a common clock

###Examples:
[ correct ] Amazon.com
</br>
[ correct ] Cassandra DB ( Non relational NoSQL DB with horizontal scaling )
</br>
[ Incorrect ]. My computer: Processors and drivers share a common clock
</br>

##Distributed Storage

###Strategies:
	Simple ones (Based on relational paradigm with tweaks)
-	Read Replication: Single master, multiple followers. Good for Read heavy systems. May sacrifice consistency as write updates may not propagate fast enough.
Bottleneck at the main node’s write operations.
-	Sharding: Multiple bins/shards based on keys with each shard following read-replication. Solves the bottleneck on write ops by dividing write traffic.
Problems: limited data model (key must be common across all tables), limited data access capability (can only query based on key or else do a scatter/gather)

-	Consistent Hashing/Distributed Hash Table (DHT)/Dynamo style DB (Amazon internal)/cassandra DB

-	Hash the key. Nodes distributed in a ring with tokens/hash ranges assigned. The key is distributed based on hash value. Data is balanced. No Single master

-	Very scalable. Always online (Need not shut it down to introduce new nodes)
But data redundancy is gone. Single copy of data at each node, so may get lost. Solution: Copy to three neighbor nodes instead of one.  
We introduced a problem! Consistency will take a hit. 
So there is a tradeoff

```
R+W>N
```

R -  no of nodes that must agree on a read\
W - no of nodes that successfully accept a write.
N - Total no of replicas (In our case=3)

We may sacrifice consistency in this case. (may not always get the most recent write update on a new read) if we want better latency. (Do not wish to wait for read/write confirmations)

###Why use consistent hashing?
Scale, good for transactional data (many reads and writes), always online

```
CAP Theorem
C – consistency ( When a read is performed, I am getting the last recently updated write?)
A – Availability ( Am I always getting a response to any read/write)
P – Partition tolerance ( Some of the nodes may not be able to talk/respond to others for a period of time) – Am I able to handle the mess when partition has been healed?
```
###Systems cannot have these 3 all together.

In distributed systems, we are anchored in P. So we must choose and trade-off b/w C and A.

In the midst of a partition, One can only choose one of Availability (Answer with an inconsistent/non up-to-date version) or Consistency (Choose not to answer until I have a consistent version).


##Distributed Transactions
```
ACID Transactions
A – Atomic. Complete or not at all.
C – Consistent.  After a query, leave the DB uncorrupted.
I – Isolated. One transaction completes, only then another transaction can access that data.
D – Durable. Transactions are persistent. Can be checked from DB once they are completed.
```

Atomicity in transactions can hurt throughput (Slow you down). So can be sacrificed by handling/responding to failure cases separately 

##Distributed Computation:
Computation on distributed storage.

###Paradigms:
- Scatter/Gather: Scatter computation on multiple nodes and gather results.
- MAP Reduce:

Break problems into the kinds of pieces that lend themselves well to distributed computation.
2 functions: Mapper and reducer
we're trying to move our compute to where our data is, not move the data around, and get all our work done in these two functions.

Example on WordCount:
</br>
Key is poet name. Value is the Poems/text.
Feed it to Mapper:
It will tokenize the text and store it as key value pairs (key is each word and value is 1). Every time it sees a word, it stores it like this (Dumb! But scalable and can be done independently across nodes)
</br>
Mapper then gives it to shuffler:
Shuffle the key values such that values with common keys get collected at one place so we've got good data locality. (Again can be done largely independently)
</br>
Shuffler then gives it to reducer:
Reduces by accumulating all values for each key (In our case: add them up, so we get a count associated with each word)
(Reducing is easy as shuffler brought values for same keys together)
</br>
Reduce can be run multiple times to get the final answer. Can have multiple reducers running simultaneously as well.
</br>
Tip: Hadoop uses this paradigm.



## Well, That's All for today, folks! See you next time.
Post your doubts and I will try to clarify!

[Prev Entry](https://swatigupta1997.github.io/blog/2019/06/08/basic-statistics-functions-in-python/)


{% if page.comments %}

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = https://swatigupta1997.github.io/blog/2020/06/28/distributed-systems-notes/ // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = {{ page.title }}; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://swatiguptablog-1.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            

{% endif %}


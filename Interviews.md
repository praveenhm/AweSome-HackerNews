##### Interviews website

- [free programming books](https://github.com/vhf/free-programming-books/blob/master/free-programming-books.md)
- [Interview website](http://www.geeksforgeeks.org/)
- [deligtful puzzles](http://gurmeet.net/puzzles/)
- [first time Interview ](http://firstround.com/article/The-anatomy-of-the-perfect-technical-interview-from-a-former-Amazon-VP)

- [fucked up google interview](https://news.ycombinator.com/item?id=6243627)

- [why secure email is difficult](https://news.ycombinator.com/item?id=6243936)

- [I will not do another tech interview](https://news.ycombinator.com/item?id=6251087)

- [Algorithms](https://news.ycombinator.com/item?id=6283663)

- [Hire right](https://news.ycombinator.com/item?id=6432781)

- [startup interview process](https://news.ycombinator.com/item?id=6454140)

- [Hadoop interview questions](http://www.fromdev.com/2010/12/interview-questions-hadoop-mapreduce.html)

- [Core java blog, good for interview](http://vanillajava.blogspot.com/)

##### Interview questions,

- [coding interview](https://news.ycombinator.com/item?id=6559404)

- [40 collections questions](http://www.javacodegeeks.com/2013/02/40-java-collections-interview-questions-and-answers.html)
- [Java interview questions](http://javaadmin.com/category/interview-questions/)

- [Java interview questions](http://javarevisited.blogspot.com/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html)

- [online resouces](https://www.quora.com/Job-Interview-Questions/What-are-good-free-online-resources-to-prep-for-code-interviews)

Threads,

- [concurency](https://news.ycombinator.com/item?id=6560214)

#### startup interviews,
- [why startup ask math puzzle to code](https://news.ycombinator.com/item?id=6583580)

- [question to ask your poetential employer](https://news.ycombinator.com/item?id=6701707)
 

#### Hiring software developers,

- [Hiring software developers](http://hesh.am/2013/11/hiring-software-developers/)


#### Algorithms,
-[Algorithms](http://interactivepython.org/courselib/static/pythonds/index.html)
- [DataStructures and algorithms](http://www.cs.usfca.edu/~galles/visualization/Algorithms.html)

#### Java best practices,

-[Java best practices](http://www.javapractices.com/home/HomeAction.do)


#### Interview prep,

- [Interview prep for google](http://steve-yegge.blogspot.ca/2008/03/get-that-job-at-google.html)
- [hadoop prep for big data](http://horicky.blogspot.com/2010/10/bigtable-model-with-cassandra-and-hbase.html) 


#### Garbage collection,

- [Java garbage collection distilled, good one on GC](http://www.infoq.com/articles/Java_Garbage_Collection_Distilled)

- [Inside the java virtuall machine, Garbage collector](http://www.artima.com/insidejvm/ed2/gcP.html)








The One Commandment of multithreaded programming,
1. Thou Shalt Not touch shared data without synchronization.
  You must know what data is shared, and you must synchronize all access to shared data
(with one exception, when all access is read-only).

2. Thou Shalt minimize and reduce shared mutable data as much as possible, in the 
design stage.Sometimes just making new copy and passing that around might not cause that much of 
a performance penalty vs the time spent debugging synchronization problems.

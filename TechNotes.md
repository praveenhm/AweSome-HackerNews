-[batch and streaming 102](https://www.oreilly.com/ideas/the-world-beyond-batch-streaming-102)


###Spark vs Flink

Both tools are receiving wide adoption, with an edge to Spark for batch/bounded processing, and to Flink for 
streaming/unbounded processing (in particular, as Flink support native streaming and Spark relies on micro-batching, 
which incurs a latency penality that may inhibit some usecases). More conceptually, Flink is an explicit inheritor of 
Google's Dataflow (now rebranded Beam) model, whereas Spark's novelty comes from its resilient distributed datasets.

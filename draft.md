## Strand information in RNA seqeuncing

One of the major improvements that has occured in RNA seqeuncing in recent years has been the development of approaches that retain information about the strand of origin in the final seqeuncing library. These include X, Y, and Z, to name a few.

One of the challenges in dealing with this, though, is that many times aligners and other downstream processing tools are not "smart" enough to be able to tell whether or not the strand infomration was retained in the data. This can result in unintended consequences, such as:

- 


Below I'd 



For pair-end RNA-seq, there are two different ways to strand reads (such as Illumina ScriptSeq protocol):

1++,1–,2+-,2-+
read1 mapped to ‘+’ strand indicates parental gene on ‘+’ strand
read1 mapped to ‘-‘ strand indicates parental gene on ‘-‘ strand
read2 mapped to ‘+’ strand indicates parental gene on ‘-‘ strand
read2 mapped to ‘-‘ strand indicates parental gene on ‘+’ strand

This is called "forward" by htseq, and 1 by featurecounts.


1+-,1-+,2++,2–
read1 mapped to ‘+’ strand indicates parental gene on ‘-‘ strand
read1 mapped to ‘-‘ strand indicates parental gene on ‘+’ strand
read2 mapped to ‘+’ strand indicates parental gene on ‘+’ strand
read2 mapped to ‘-‘ strand indicates parental gene on ‘-‘ strand

This is called "reverse" by htseq, and 2 by featurecounts.



For single-end RNA-seq, there are also two different ways to strand reads:

++,–
read mapped to ‘+’ strand indicates parental gene on ‘+’ strand
read mapped to ‘-‘ strand indicates parental gene on ‘-‘ strand

This is called "forward" by htseq, and 1 by featurecounts.


+-,-+
read mapped to ‘+’ strand indicates parental gene on ‘-‘ strand
read mapped to ‘-‘ strand indicates parental gene on ‘+’ strand

This is called "reverse" by htseq, and 2 by featurecounts.



The Illumina truseq stranded is '1+-,1-+,2++,2--'

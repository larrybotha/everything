![[formal-methods-amazon.pdf]]

![[To a first approximation, we can say that accidents are...]]

## Takeaways

- as in [[Black Swan Event]]s, humans are poor at estimating events on the long tail of distributions
- AWS developers use TLA+ as their language of choice for designing complex systems
	- the [TLC Model Checker](https://lamport.azurewebsites.net/tla/toolbox.html) automates much of the work that would be tedious using maths alone
	- PlusCal is a more C-like language variant of TLA+ which developers often find easier to read, but can sometimes lack expressiveness that TLA+ offers
-  a formal specification is precise, short, and can be explored and experimented upon with tools
- *the investment he made in writing and checking the formal TLA+ specifications was both more reliable, and also less time consuming than the work he put into writing and checking his informal proofs. Therefore, using TLA+ in place of traditional proof writing would likely have improved time-to-market in addition to achieving higher confidence on system correctness* - pg 7-8
- *We have adopted the practice of first writing a conventional prose design document, then incrementally refining parts of it into PlusCal or TLA+. Often this gives important insights without ever going as far as a full specification or model checking*
- a verified design doesn't guarantee a correct implementation in code - humans still need to write it. Nonetheless, TLA+ helps in the following ways:
	- formal methods help get the design right
		- the design is the first step to getting the code right
		- a broken design is likely going to lead to broken code 
		- implementing a broken design may deceive a developer into thinking they've got a correct implementation
		- developers are unlikely to realise a design is broken while writing code
	- formal methods help devs gain a better understanding of the design, which leads to better implementations 
	- formal methods help devs write better "self-diagnosing code"
		- AWS has found that pervasive use of assertions is a good way to reduce system errors 
		- assertions check small system [[invariant]]s - finding good invariants is not easy, but formal methods help find these invariants

## links and resources

- https://www.infoq.com/presentations/aws-testing-tla
- https://awsmaniac.com/how-formal-methods-helped-aws-to-design-amazing-services/
- https://medium.com/software-safety/using-tla-to-model-cascading-failures-5d1ebc5e4c4f

### From the PDF

[1] Barr, J. Amazon S3-The First Trillion Objects. Amazon Web Services Blog. June 2012; http://aws.typepad.com/aws/2012/06/amazon-s3-the-first-trillion-objects.html

[2] Barr, J. Amazon S3-Two Trillion Objects, 1.1 Million Requests per Second. Amazon Web Services Blog. March 2013; 

http://aws.typepad.com/aws/2013/04/amazon-s3-two-trillion-objects-11-million-requests-second.html

[3] Holloway, C. Michael. Why You Should Read Accident Reports. Presented at Software and Complex Electronic 

Hardware Standardization Conference, July 2005; 

http://klabs.org/richcontent/conferences/faa_nasa_2005/presentations/cmh-why-read-accident-reports.pdf

[4] Lamport, L. The TLA Home Page; http://research.microsoft.com/en-us/um/people/lamport/tla/tla.html

[5] Joshi, R., Lamport, L., et al. Checking Cache-Coherence Protocols With TLA+; http://research.microsoft.com/pubs/65162/fmsd.pdf

[6] Patterson, D., Fox, A., et al. The Berkeley/Stanford Recovery Oriented Computing Project; http://roc.cs.berkeley.edu/

[7] Zave, P. Using lightweight modeling to understand Chord; In ACM SIGCOMM Computer Communication Review volume 42 number 2, April 

2012; http://www2.research.att.com/~pamela/chord.html

[8] Newcombe, C. Debugging Designs. Presented at the 14th International Workshop on High Performance Transaction Systems, Monterey 

2011; http://hpts.ws/papers/2011/sessions_2011/Debugging.pdf and associated specifications; 

http://hpts.ws/papers/2011/sessions_2011/amazonbundle.tar.gz

[9] Lamport, L. Fast Paxos. Distributed Computing, Volume 19 Issue 2, October 2006, 79-103; http://research.microsoft.com/pubs/64624/tr-2005-112.pdf

[10] Lamport, L., Sharma, M., Tuttle, M., Yu, Y. The Wildfire Challenge Problem, Compaq 2001; http://research.microsoft.com/en-

us/um/people/lamport/pubs/wildfire-challenge.pdf

[11] Batson, B., Lamport, L. High-Level Specifications: Lessons from Industry, March 2003; http://research.microsoft.com/en-

us/um/people/lamport/pubs/high-level.pdf

[12] Lamport, L. The Wildfire Challenge Problem ; http://research.microsoft.com/en-us/um/people/lamport/tla/wildfire-challenge.html

[13] Lamport L., Merz, S. Specifying and Verifying Fault-Tolerant Systems. In Proceedings of the Third International Symposium on Formal 

Techniques in Real Time and Fault Tolerant Systems, September 1994; http://research.microsoft.com/en-us/um/people/lamport/pubs/lamport-ftrtft94.pdf

[14] Supported Operations in DynamoDB: Strongly Consistent Reads; 

http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/APISummary.html

[15] Lamport, L. Checking a Multithreaded Algorithm with +CAL; In Proceedings of Distributed Computing: 20th International Symposium, DISC 

2006; http://research.microsoft.com/en-us/um/people/lamport/pubs/dcas.pdf

[16] Brooker, M. Exploring TLA+ With Two-Phase Commit; http://brooker.co.za/blog/2013/01/20/two-phase.html

[17] Kudrjavets, G., Nagappan, N., Ball, T. Assessing the Relationship between Software Assertions and Code Quality: An Empirical 

Investigation; http://research.microsoft.com/pubs/70290/tr-2006-54.pdf

[18] Tasiran, S., Yu, Y., Batson, B., Kreider, S. Using formal specifications to monitor and guide simulation. In Proceedings of the 3rd IEEE 

International Workshop on Microprocessor Test and Verification, 2002; http://research.microsoft.com/apps/pubs/default.aspx?id=65169

[19] Newcombe, C., Why Amazon Chose TLA+, in Abstract State Machines, Alloy, B, TLA, VDM, and Z Lecture Notes in Computer Science 

Volume 8477, 2014, pp 25-39; http://link.springer.com/chapter/10.1007%2F978-3-662-43652-3_3

[20] Bolosky, W., Douceur, J., Howell, J. The Farsite project: a retrospective; http://research.microsoft.com/apps/pubs/default.aspx?id=74211

[21] Abrial, J. Formal Methods in Industry: Achievements, Problems, Future; http://www.irisa.fr/lande/lande/icse-proceedings/icse/p761.pdf

[22] Lu, T., Merz, S., Weidenbach, C. Towards Verification of the Pastry Protocol Using TLA+; 

http://www.loria.fr/~merz/papers/forte2011pastry.html
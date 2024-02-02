![[formal-methods-amazon.pdf]]

![[To a first approximation, we can say that accidents are...]]

## Takeaways

- as in [[Black Swan Event]]s, humans are poor at estimating events on the long tail of distributions
- AWS developers use TLA+ as their language of choice for designing complex systems
	- the [TLC Model Checker](https://lamport.azurewebsites.net/tla/toolbox.html) automates much of the work that would be tedious using maths alone
	- PlusCal is a more C-like language variant of TLA+ which developers often find easier to read, but can sometimes lack expressiveness that TLA+ offers

## links and resources

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
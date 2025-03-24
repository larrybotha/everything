---
tags:
  - resource/course
---

Link: https://programs.clearerthinking.org/question_of_evidence.html

- evidence doesn't confirm theories with absolute certainty
    * evidence only suggests whether a theory is more or less likely to be true
- it's more accurate to consider the _relative_ strength of evidence

## The question of evidence

Ask the question

> How much more likely am I to encounter this evidence if my theory is true
    than if it is false?

- i.e. am I more likely to see observation X if my theory is true than if it is
    false?
- if you are more likely to encounter the evidence if your theory is true than if
    it were false, it supports your theory. Conversely, if it is more likely to
    occur when your theory is false, it contradicts your theory. The evidence
    may also have no correlation with your theory if it equally likely to occur
    whether your theory is true or false
- a theory may be strongly or weakly supported by evidence, strongly or weakly
    contradicted by evidence, or have no correlation with evidence

According to probability theory, **this is the only question that can accurately
evaluate the strength of evidence**

The degree to which the evidence supports or contradicts the theory is important -
one should take with a pinch of salt evidence that only mildly supports or
contradicts a theory, whereas one should pay attention to evidence that strongly
supports or contradicts a theory

### incorrect phrasings

- Is the evidence consistent with my theory?
	- false dichotomy - evidence contradicts or supports theories across a spectrum
- How likely is this evidence given that my theory is true?
    - assumption that the theory is true - no place to consider that the theory is false
    - the likelihood of the evidence under alternate hypotheses is not considered

### tips

- think of the question of evidence as a scale
	- the probability of the evidence given your theory is true
	- the probability of the evidence given your theory is false
- make your best guess for probabilities
	- gauge the relative strength of the evidence - is it strong, moderate, or weak?
- adjusting your confidence doesn't necessarily mean changing your mind
	- a 10% increase in confidence on 5% confidence is still a low confidence
- consider alternate possibilities
	- are there any other possible explanations for the piece of evidence? If so, what are they?

### example

- let's assume we have a sample of 15 people, 5 of which exhibit symptom X
    i.e. 33% have the symptom, 66% do not, resulting in a ratio of 1:2 - for
    every 1 person that has symptom X, 2 do not
    This is the _ratio of people who have the symptom_ versus those who don't,
    distinct from the fraction of people who have the symptom, which is 1/3
- there exists a test s.t. it produces the following results:
    * 4 in 5 people who do have symptom X test positively for symptom X
        i.e. 1 in 5 yield a false negative, an 80% / 20% ratio of accurate
        outcomes
    * 9 in 10 people who do not have symptom X test negatively for symptom X
        i.e. 1 in 10 yield a false positive, a 90% / 10% ratio of accurate
        outcomes
- question of evidence:
    * how much more likely is it that the test will yield a positive result for
        someone that _does_ have symptom X than if they didn't?
    * i.e. how much more likely is a true positive result than a false positive
        result?
- first, how likely are we to get an accurate positive result for someone who
    _does_ have symptom X
    i.e a true positive (80% of those that _do_ have symptom X) vs
    false positive (10% of those that _don't_ have symptom X):
    * 80% / 10% = 8 => the test is 8 times more likely to produce a true positive
    than a false positive
- second, how likely are we to get an inaccurate negative result for someone
    who _does_ have symptom X?
    * 20% / 90% = .222 => the test is .222 times more likely to produce a false
    negative than a true positive, or
    1/(20% / 90%) = 4.5 => the test is 4.5 times more likely to produce a true
    negative than a false negative
- a patient comes in for a screening - we don't know whether they have the symptom
    or not, but based on our existing patients, we expect a 1:2 odds that they
    have the symptom
    - the patient is then screened, and the test returns positive for the symptom
    - this information can now update our expectation:
        * the test is 8 times more likely to produce a true positive for someone
            having the symptom
        * the odds that an untested person has the symptom is 1 in 2, or 50%
        * (80% / 10%) * (33% / 66^) = 8 * (1/2) = 4 => our expectation should be
            that it is 4 times more likely that the person _does_ have the
            symptom as per the test result than being falsely identified
- similarly, for a patient who has received a negative result:
    * (20% / 90%) * (33% / 66%) = (2/9) * (1/2) = 1/9 => our original expectation
        that they are twice as likely _not_ to have the symptom can be updated to
        being 9 times more likely they _do not_ have the symptom than being
        falsely identified
- this process is known as Bayesian inference, or Bayesian updating

## related

- [[Question of evidence]]


## links and resources

- https://mathcenter.oxford.emory.edu/site/math117/probSetBayesTheorem/
- https://www.bayesrulesbook.com/
- https://www.mathsisfun.com/data/bayes-theorem.html
- https://www2.math.upenn.edu/~mmerling/math107%20docs/practice%20on%20Bayes%20solutions.pdf













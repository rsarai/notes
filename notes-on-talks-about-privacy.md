# Data Privacy Talks
- [Pycon Ireland 2017: Data Anonymization - Bartlomiej Uscilowski](#Pycon-Ireland-2017-Data-Anonymization)
- [Katharina Rasch: What every data scientist should know about data anonymization | PyData Berlin 2016](What-every-data-scientist-should-know-about-data-anonymization)
- [Keeping Your Data Secure While Learning From It - Andreas Dewes and Katharine Jarmul](#Keeping-Your-Data-Secure-While-Learning-From-It)
- [Andreas Dewes - Fairness and transparency in machine learning: Tools and techniques](#Fairness-and-transparency-in-machine-learning)
- [Dustin Ingram: Data Protection for Developers: Past, Present, and Future](#Data-Protection-for-Developers)

# Pycon Ireland 2017 Data Anonymization
## Resume
Today’s data contains personally identifiable information (PII), which has to be protected. The protection methods include strong encryption, authentication and authorization, and anonymization. The latter, the data anonymization, removes or modifies sensitive data in an irreversible transformation, preserving sufficient data characteristics to enable analysis, aggregations and evaluation while protecting privacy. In our talk we will discuss using two modules: faker and mimesis, for anonymizing customer data. The primarily goal of both modules is producing synthetic data for development and quality assurance. However, the modules can be used for anonymizing data sets, preserving data characteristics, such as uniqueness and consistency. The data formats of, for example, email addresses, urls, dates, are also preserved

## Content

### Why
- Protect sensitive and especially Personally Identifiable Information PII
- Regulatory Compliance (EU vs US laws)
- Minimize data disclosure in case of data breach
- Examples of PII

### Requirements
Raw data -> Removal | Masking | Tokenisation -> Analyst Data -> Analysis -> Diff Provacy | K-anonymity -> Publish

- One way transform
- Preserve:
    - Integrity
    - Uniqueness
    - Distribution
    - Semantic relationships
- Methods
    - Removal
    - Masking
    - Tokenisation (Substitution)
    - Differential Privacy (Out of scope)
    - K-anonymity (Out of scope)

### Modules
- mimesis: generate, tokenize
- faker: generate, tokenize
- anonymize: masking, removal
- srubadub: removal, tokenize, etc

### Generate Data
- Using Faker
- User model
- Different types on data

### Anonymization
- Mimesis and faker. Create a mapping between the original data and the anonymized data.
- One way transfer, the original value can't be restored.

### Limitations
- Works for data processed in one go
- Hard to ensure consistency between runs
- Good for QA, but no anonymization
- Define custom provider
- Protect sensitive information
- Preserve integrity, distribution and semantics


# What every data scientist should know about data anonymization
Katharina Rasch: What every data scientist should know about data anonymization | PyData Berlin 2016
https://www.youtube.com/watch?v=O3hxp117EHs

## Resume
There are numerous examples of data anonymization gone horribly wrong - the most prominent one might be the netflix prize, where researchers were able to uniquely identify users by combining netflix user data with imdb reviews. Let's learn from their mistakes and look at some of the measures you can take to better anonymize data before you share it with others.

Outline:
    - Look at some of the examples where data anonymization was broken and identify what went wrong
    - What is the state of the art for data anonymization and can you be sure to be safe if you follow it?
    - How does anonymization affect the possibilities for data mining/machine learning on the data?

This talk is aimed at people who want release open data or want to share sensitive data between departments.

## Content
Cities and Scientists are being encouraged to share the data they used, this leads to data breaches.

- Introduction
- Let's anonymize a dataset
- Utility of anonymized data
- Alternative: the interactive model
- Practical tips and standards

Sensitive information -> Same definition of the GDPR

### Assumptions
- Publish raw data, not statistics
- Want to minimize the risk for privacy breaches
- All record owners have equal right to privacy
- Adversaries are determined, resourceful and technically competent
- The de-anonymization algorithms that attackers will use are unknown
- Assume adversary has access to additional data (external datasets public or closed, personal knowledge about target, etc)

### Fact
- In the US, 63% of people are likely to be uniquely identifiable by birthdate, sex, zip code.
- Age, sex, zip code, ethnicity, education, etc, are called quasi identifiers

### K-anonymity
There must always be at least k record for each equivalence group present in the dataset.

equivalence group = all records with same combination of quasi-identifiers

### Increase K Through
- Generalization (age in ranges, remove specific location)
- Suppression (remove record definitely)

### l-diversity
There must always be at least l distinct values for each sensitive attribute and equivalence group

### t-closeness
Distribution of a sensitive attribute in any equivalence group must be close to this attribute's distribution in whole dataset

### Example with the dataset: adult
- Arx de-identification software
- Standard settings
- Logistic regression

### Fact
Most anonymization methods fail for high-dimensional, sparse datasets. Amazon's purchases.

Netflix prize privacy breach

Mobile phone location data

### Differential Privacy
The risk to one's privacy should not substantially increase as a result of participating in a statistical database.

### There is no one-size-fits-all manual
what data do you want to protect?
what is impact if you fail to protect?
what kind of knowledge / methods could adversary use?
what is the use case of the people using dataset?
is enough utility retained after anonymization?

### Standards
- HIPAA Safe Harbour (US, medical data) at most first three digits of zip (fewer if less than 20k people) for all dates use only years, group ages 90+ no names, phone numbers, social security numbers etc (unique for approximately 0.04% of US residents)

- SAFE (Germany, census 2011, statistics) there must always be at least three records for each equivalence group present in the dataset, suppress smaller groups


# Keeping Your Data Secure While Learning From It
(PyCon.DE 2018: Keeping Your Data Secure While Learning From It - Andreas Dewes and Katharine Jarmul)
[link](https://www.youtube.com/watch?time_continue=1&v=i-embbaJX_A)

## Resume
We will discuss anonymization and pseudonymization techniques that you can apply to your data to keep it secure and comply with the law(s) while still being able to gain useful insights from it.

Why protect data?
Pseudonymization vs. anonymization: What's the difference?
Pseudonymization: Techniques & real-world examples
Problems and risks when pseudonymizing data
Anonymization: Approaches & real-world examples
Problems and risks when anyonymizing data
Takeaways and summary
We will show concrete Python implementations of various techniques and use example data sets to show how applying pseudonymization and anonymization will affect our ability to do machine learning / data science.

## Content
- Overview
    - Pseudonymization
    - Anonymization

## Reasons for thiking about data security
- Ethical Reasons
    - Profissionality
    - Users privacy
- Legal Reasons
    - Regulations
- Business reasons
    - Leaking data causes damages to reputation
    - Lawsuits

## Ways to Secure data
- Homomorphic Encryption
- Pseudonymization
- Anonymization
- Federated Learning

Show examples of raw, pseudoanonymized and anonymized

## Pseudonymization
- Mapping-based: use a table/databse and a stochastic or deterministic mapping to produce pseudonyms from input data
- Cryptography-based: use cryptographic techniques to produce a deterministic but pseudo-random mapping from input data to psedonimos

### Structure preserving tecniques
- IP address are considered personal data
- Other examples with SVM

## Anonymization
- K-anonymity: aggregate data such that every group contains at least k entries.
- examples with a normal database
- Good example
- K-anonymity mondrian
- l-diversity
- t-closeness

## Differential Privacy
- Method to quantify the privacy loss of a given method
- It measures how likely it is that a prababilistic anonymization method will yield the same result for slightly different data sets
- Mathematically strict definition that doesn't need specification of sensitives attributes
- Good Example


# Fairness and transparency in machine learning
Andreas Dewes - Fairness and transparency in machine learning: Tools and techniques
[link](https://www.youtube.com/watch?v=6b5GbmnXdOU)

## Resume
**Description**: This talk will try to answer a simple question: When building machine learning systems, how can we make sure that they treat people fairly and can be held accountable? While seemingly trivial, this question is not easy to answer, especially when using complex methods like deep learning. I will discuss tools and techniques that we can use to make sure our algorithms behave as they should.

**Abstract**: When working with personal data, we need to make sure that our algorithms treat people fairly, are transparent and can be held accountable for their decisions. When using complex techniques like deep learning on very large datasets, it is not easy to prove that our algorithms behave they way we intend them to and e.g. do not discriminate against certain groups of people. In my talk, I will discuss why ensuring transparency and fairness in machine learning is not easy, and how we can use Python tools to investigate our machine learning systems and makre sure they behave they way they should.

- Introduction: Why you should care about this (EU Data Protection Directive)
- What kind of problems can occur in machine learning systems (bias in the input data, leakage of sensitive information into the training data, hidden usage of protected attributes by the algorithm)?
- How can we measure and correct for bias in our systems (certifying and removing disparate impact)?
- How can we understand the decisions that our algorithms make (perturbation analysis, simplified modeling, blackbox testing)?
- How can we design our machine learning systems to make sure they're compliant and accountable (anonymization of data, monitoring of outcomes, auditing of algorithms)?
- Outlook: The future of transparency and accountability in machine learning

## Content
- Fairness
- Discrimination
- Calculating Discrimination: disparate impact

...


# Data Protection for Developers
Dustin Ingram: Data Protection for Developers: Past, Present, and Future
[link](https://www.youtube.com/watch?time_continue=2&v=hCAGvsyLEN4)

# Resume
n 1970, the German state of Hesse enacted what is widely considered the very first data protection laws. Nearly fifty years later, the European Union has implemented the strongest, most comprehensive data protection regulation ever. This talk gives a crash course on data protection and the GDPR.

# Django Con Europe 2018
- [Protecting Personal Data with Django (because it's the law)](#protecting-personal-data-with-django-because-it-s-the-law)
# Django Con US 2018
- [Pseu, Pseu, Pseudio. Pseudonymization in Django](#pseu-pseu-pseudio-pseudonymization-in-django)
- [Finally Understand Authentication in Django REST Framework by William S. Vincent](#finally-understand-authentication-in-django-rest-framework-by-william-s-vincent)
# Lead Dev London 2019
- [Communicating and documenting architectural decisions - David Ayers](#communicating-and-documenting-architectural-decisions)
# PyCon 2017
- [Modern Python Dictionaries A confluence of a dozen great ideas](#modern-Python-Dictionaries-A-confluence-of-a-dozen-great-ideas)
# PyData Berlin 2016
- [Katharina Rasch: What every data scientist should know about data anonymization | PyData Berlin 2016](What-every-data-scientist-should-know-about-data-anonymization)
# Others
- [Keeping Your Data Secure While Learning From It - Andreas Dewes and Katharine Jarmul](#Keeping-Your-Data-Secure-While-Learning-From-It)
- [Andreas Dewes - Fairness and transparency in machine learning: Tools and techniques](#Fairness-and-transparency-in-machine-learning)
- [Dustin Ingram: Data Protection for Developers: Past, Present, and Future](#Data-Protection-for-Developers)
- [Pycon Ireland 2017: Data Anonymization - Bartlomiej Uscilowski](#Pycon-Ireland-2017-Data-Anonymization)
------

# Pseu, Pseu, Pseudio. Pseudonymization in Django.

## What is Pseudonymization
A data de-identification procedure

## Why would you need this
Protect users identities
GDPR

## Personal Data AKA PII - (Personal Identifier Information)
- Full Names
- Home Addresses
- Email
- Telephones

## Data Privacy Techniques

### Most Commons
#### Pseudonymization
Approach for treating personal data so that it can't be used to identify indivial users without the use of additional information. (Replacing names)
#### Anonymization
Permanent de -identification of a data set so no party will be able to identify the indiduals.

### Pseudonymization Tecniques
- Data Masking
- Approximation (birth date, not save full date)
- Encryption
- Tokenization

## Simple Implementation
### Masking
- User with name field
- Creates a pseudonyms fields like _name, these fields show a masked value
- Update queryset
- Exclude Pseudonyms
- Update admin

### Data masking via custom fields
-

https://www.youtube.com/watch?v=wRro4xv8n6k
https://www.cuttlesoft.com/data-pseudonymization-in-django/


# Finally Understand Authentication in Django REST Framework by William S. Vincent
- https://wsvincent.com/
- [Slides](https://docs.google.com/presentation/d/1elsMKIFDw1ZcCyeSn9kr7cwvwC7IQnnfAOsWiPN9t64/edit#slide=id.g409c6afe0e_0_15)

## API (**A**pplication **P**rogramming **I**nterfaces)

## Restfull APIs
- Stateles
- HTTP methods
- Url endpoint
- Json x Xml

## Django + DRF

## HTTP HyperText Transfer Protocol
- client <-> server
- CRUD
- Codes

### HTTP Anatomy
- Start/Status line
- Header
- Body

## Rest API Endpoint
- BasicAuthentication
- SessionAuthentication
- TokenAuthentication
- RemoteUserAuthentication

## Json Web Tokens

## DRFx
https://github.com/wsvincent/drfx


# Protecting Personal Data with Django (because it's the law)
[link](https://www.youtube.com/watch?v=b6KEoNVKFxM)
## GDPR
### Terms
    - Any information realting to an identified or identifiable natural person.
### Rights
    - Company must provide you the data they have about you.
    - Transparency, access, rectification, erasure (delete user on backup?), data portability, restriction of processing
### Tasks
    - By design and default: taking into the account the state of the art, the cost of implementation. (secure applications)
        - Separate personal data completely
        - Separate sensitive data
        - Encrypt sensitive data
        - Restrict access
    - Erase

# The Hardest Scaling Challenge of All
[link](https://www.youtube.com/watch?v=86fqsVWngHI)

## Scale
- To climb, ascend;
- To progress in a graduated series;
- To be a gravity defying;

## Outline
- Communication
- Prioritization & Time management
- Delegation
- Personal Development


# Communicating and documenting architectural decisions
[link](https://www.youtube.com/watch?v=rwfXkSjFhzc)


1. Lightweight Architectural Decision Records
2. Enterprise Architecture Guilds
3. Build Reference Implementations


## Lightweight Architectural Decision Records

> "Why did we decide to do it this way?"

- The decision is not socialized to the team or the organization, resulting in the question above.
- The decision is not recorded, also resulting in the question above, because the team doesn't know what led to that decision.


> Why it's important to document?

- It's great to understand the context of the team/project/code at the moment of the decision.

## ADRs (Architectural Decision Records)

Michael Nygard develop this idea of documenting this decisions along with the code in a lightweight manner.

_(Here David talks "bad" about wikis to prove that putting the documentation on the code is a good idea)_

ARDs are:
- Text document, usually markdown.
- One ADR per file.
- Should be short and straigth to the point.
- Filename named like django migrations
- Saved in a ADR folder at the top level
- ARDs have a status: accepted, deprecated
- ARDs have a context
- ARDs have a decision
- ARDS have consequences: migrations needed, things that this decision don't support, short time consequences, benefits.
- Should be short and to the point

ADRs == Awesome _(David's point)_
Good way to store decisions
Approved by: TW Technology Radar

## Enterprise Architecture Guilds
Complex decisions when a team needs to get together to define a complex architecture.
- Writting ADRs
- Creating the teams (SIGs?)
- Running the team

The team acts as a Architecture Review Board. This team helped with the problem of socializing decisions.

_(This seems to be only applicable for big projects.)_

## Build Reference Implementations
Reference application baked in best practices. _(Seems like vinta's boilerplate)_

## References
- http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions
- https://adr.github.io/
- https://github.com/joelparkerhenderson/architecture_decision_record
- https://github.com/npryce/adr-tools


# Apps, Algorithms and Abstractions: Decoding our Digital World
[link](https://skillsmatter.com/skillscasts/11782-apps-algorithms-abstractions)

Everything between sending and receiveing cat pics.

- Cellphone Signal
  - Radio Signals
  - Using radio to transmit information e.g: tetris
    - Interference on radio waves: Frequency modulation, amblitube modulation, phase modulation



# Automating Code Quality: Next Level
_Kyle Knapp_
[link](https://www.youtube.com/watch?v=iKAaNaVpJFM&feature=youtu.be)

## How to Automate
- Checks
  - flake8
  - pylint
  - coverage
- Run on CI and CodeCov
- Trigger or not PR

## Benefits
- Enforces quality
- Improves efficiency
- Protect developers from mistakes

## Lesser-know tools
- pydocstyle
- doc8
- mypy

### mypy
Static Type check
Helps better document code and catch bugs

### pylint
Static code analysis tools
    - Check coding standards
    - Warns for stylng issues
    - Checks for potential bugs
    - Allows the creation of plugins

## Documentation tools
### pydocstyle
...



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

## Resume
n 1970, the German state of Hesse enacted what is widely considered the very first data protection laws. Nearly fifty years later, the European Union has implemented the strongest, most comprehensive data protection regulation ever. This talk gives a crash course on data protection and the GDPR.

# Modern Python Dictionaries A confluence of a dozen great ideas
Raymond Hettinger: Modern Python Dictionaries A confluence of a dozen great ideas - PyCon 2017
[[link](https://www.youtube.com/watch?v=uRKiERJr6yg)]

## Resume
Abstract Pythons dictionaries are stunningly good. Over the years, many great ideas have combined together to produce the modern implementation in Python . Speaker: Raymond Hettinger Pythons.

Pythons dictionaries are stunningly good. Over the years, many great ideas have combined together to produce the modern implementation in Python 3.6. This fun talk uses pictures and little.

## Content
Python is built around dictionaries. The various namespaces include globals, locals, module dictionaries, class dictionaries, instace dictionaries.

### Dictionry Size
Version             Dict Size           Notes
Python 2.7          280                 Scrambled
Python 3.5          196                 Randomized
Python 3.6          112                 Ordered

### Evolution: A dozen Good Ideas
In the beginning there were databases:

Name        Color       City        Fruit
-------     ---------   --------    -----------
'guido'     'blue'      'austin'    'apple'
'sarah'
'barry'
'rachel'

### Setup

```python
keys = 'guido sarah barry rachel tim'.split()
values = 'blue red orange green yellow orange'.split()
hashes = list(map(abs, map(hash, keys)))
entries = list(zip(hases, keys, values))
com_entries = list(zip(hashes, keys, values))

[(6874078819681461717, 'guido', 'blue'),
 (9068623359221365180, 'sarah', 'red'),
 (701242702487512890, 'barry', 'orange'),
 (1227228226059516264, 'rachel', 'green'),
 (8000641104112633588, 'tim', 'yellow')]
```

### How LISP would do it
```python
[
    [("guido", "blue"),
        ...],
    [("guido", "austin"),
    ...]
]
```

A list of tuples that need to be searched independently. Redundant.

### Separated Chaining
Use multiple buckets to reduce the linear seach by a constant factor.
```python
def separate_chaining(n):
    buckets = [[] for i in range(n)]
    for pair in entries:
        key, value = pair
        h = hash(key)
        i = h % n
        buckets[i].append((h, key, value))
    pprint(buckets)
```

- Structure for 2
```python
[[('guido', 'blue'), ('tim', 'red')],
 [('sarah', 'orange'), ...]]
```

Goes on for 4 and 8. Further increase the number of buckets so that some buckets are empty and most of then have one entry per bucket.

If the buckets are big enough the everyone will be in their own bucket, and the number of lookups will be exactly one.

### Dynamic Resizing
With 8 buckets and 2000 entries we would get linear searches of chains of length 250. The dictionary slows doen as it gets bigger.

The solution is to periodically resize the dictionary so that it never more than two-thrids full

```python
def resize(self, n):
    items = self.items()
    self.buckets = [[] for i in range(n)]
    for key, value in items:
        self.[key] = value
```

### Caching the Hash Value
Naive resizing is expensive because the hash values would need to be recomputed for every key. The solution is store the full hash:

```python
[(6874078819681461717, 'guido', 'blue'),
 (9068623359221365180, 'sarah', 'red'),
 (701242702487512890, 'barry', 'orange'),
 (1227228226059516264, 'rachel', 'green'),
 (8000641104112633588, 'tim', 'yellow')]
```

This makes resizes very cheap, about one-fifth as fast as a list copy!

### Faster Matching
When searching a bucket we need to know whether the target key is found. We cold test whether `key == target_key`, but that can be slow because any object can define a complex `__eq__()` method.

The solution is to have two fast early-outs:
- If two variables point to the same object, they are deemed equal. We say "identity implies equality".
- For hash tables to work at all, they follow the invariant, "if two objects are equal, then their hash values are euqal as well".

```python
def fast_match(key, target_key):
    if key is target_key:           return True
    if key.hash != target_key.hash  return False
    return key == target_key
```

### Open Addressing
All buckets go to one table, the table becames dense and there is a risk of collisions, to solve this you can use linear probing

```python
[
    ('tim', 'red'),             # 'tim' collidede with 'sarah'
    None,
    None,
    ('guido', 'blue'),
    ('rachel', 'yellow),
    None,
    ('barry', 'green'),
    ('sarah', 'orange')]
```

### Deleted Entries
Removing a key leave a hole. The solutionn is to mark the slot with a DUMMY value, to serve as placeholder. This scheme is known as **"Knuth Algorithm D"** and dates back to the late 1960.


### Multiple Hashing
The problem with linear probing is that we can end up with catastrophic linear pile-up. The solution is re-hash to other locations based on both the full hash value and on the number of probes. To make sure we use all the bits of he hash, we gradually shift in 5 bits at a time.

### Compact Dictionaries
The problem is that dict tables have a lot of empty space internally for every entry which includes a hash, key, and value.

The solution is to store the hash/key/value table densely and make a separeate, tiny spared table of indices to vector into the dense table.

```python
[
    (6874078819681461717, 'guido', 'blue'),
    (9068623359221365180, 'sarah', 'red'),
    (701242702487512890, 'barry', 'orange'),
    (1227228226059516264, 'rachel', 'green'),
    ...
]

[2, None, 1, 0, 4, 3, None]
```

The index row can be stored in only 8 bytes!

### Key-Sharing Dict
The problem is if you have several dictionaries with the same keys, then there is unnecessary repetition of the keys, hash values and indices.

### The Future has density and Great Sparsity
We can make the dict more sparse without moving any of the has/key/values entries. The Additional sparcity only costs 8 bytes and removes all hash collisions.

```python
[
    (6874078819681461717, 'guido', 'blue', 'austin', 'apple'),
    (9068623359221365180, 'sarah', 'red', 'dallas', 'banana'),
    (701242702487512890, 'barry', 'orange', 'tuscon', 'orange'),
    (1227228226059516264, 'rachel', 'green'), 'reno', 'pear'),
    ...
]

[None, 4, None, 1, None, None, 0, None, 2, None, 3, None, None, None, None, None]
```

### Odds and Ends
- Sets use a different strategy, a mix of multiple chaining and linear probing.
- Cuckoo hashing is still possible with the current desing though it is likely not going to be a win.
- Internally, dict and sets have additional logic to guard against mutation while iterating.

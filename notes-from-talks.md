# Django Con Europe 2018
- [Protecting Personal Data with Django (because it's the law)](#protecting-personal-data-with-django-because-it-s-the-law)
# Django Con US 2018
- [Pseu, Pseu, Pseudio. Pseudonymization in Django](#pseu-pseu-pseudio-pseudonymization-in-django)
- [Finally Understand Authentication in Django REST Framework by William S. Vincent](#finally-understand-authentication-in-django-rest-framework-by-william-s-vincent)
# Lead Dev London 2019
- [Communicating and documenting architectural decisions - David Ayers](#communicating-and-documenting-architectural-decisions)

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

Michael Nygard develop this idea of documenting this decision along with the code in a lightweight manner.

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

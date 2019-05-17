# Django Con Europe 2018
- [Protecting Personal Data with Django (because it's the law)](protecting-personal-data-with-django-because-it-s-the-law)
# Django Con US 2018
- [Pseu, Pseu, Pseudio. Pseudonymization in Django](#pseu-pseu-pseudio-pseudonymization-in-django)
- [Finally Understand Authentication in Django REST Framework by William S. Vincent](finally-understand-authentication-in-django-rest-framework-by-william-s-vincent)

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
# Talks List
- [Pseu, Pseu, Pseudio. Pseudonymization in Django](#pseu-pseu-pseudio-pseudonymization-in-django)

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

------
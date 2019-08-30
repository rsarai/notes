# Articles Summary

- [Anonymity: An Enhanced k -Anonymity Model for
Privacy-Preserving Data Publishing](#Anonymity-An-Enhanced-k-Anonymity-Model-for-Privacy-Preserving-Data-Publishing)
- [Anonymization in the Time of Big Data](#Anonymization-in-the-Time-of-Big-Data)


# Anonymity An Enhanced k-Anonymity Model for Privacy-Preserving Data Publishing
(a, k) - Anonymity: An Enhanced k-Anonymity Model for Privacy-Preserving Data Publishing
by Raymond Chi-Wing Won, Jiuyong Li, Ada Wai-Chee Fu and Ke Wang

## Abstract
- The k-anonymity has been introduced for protecting individuals identification. Recent studies show that a more sophisticated model is necessary to protect the association of individuals to sensitive information.
- The paper proposes an (a, k)-anonymity model to protect both identifications and relationship to sensitive data information.

## Introduction
- When a data set is released to other parties for data mining, some **privacy-preserving technique** is often **required** to reduce the possibility of **identifying sensitive** information about individuals. This is called the **disclosure-control problem** in statistics and has been studied for many years.
- Strong privacy-preserving models and designing efficient optimal and scalable heuristic solutions. The perturbing method and the k-anonymity model are two major techniques for this goal.
- The k-anonymity model assumes a **quasi-identifier**, which is a **set of attributes** that **may** serve as an **identifier** in the data set.
- Being _Q_ the **quasi-identifier**, an **equivalence class** of a table with respect to Q is a collection of all tuples in the table containing identical values for Q, making "impossible" to identify a individual user.
- The **size of an equivalence class** indicates the **strength of identification protection** of individuals in the equivalent class.
- If the number of tuples in an equivalence class is greater, it will be more difficult to re-identify individual.
- In the literature of k-anonymization, there are **two main models**. One model is **global recoding** while the other is **local recoding**.
    - A lower level domain in the hierarchy provides more details than a higher level domain. For example, birth date in D/M/Y (e.g. 15/Mar/1970) is a lower level domain and birth date in Y (e.g. 1970) is a higher level domain. Generalization replaces lower level domain values with higher level domain values. For example, birth D/M/Y is replaced by M/Y.
    - **Global recoding**: All values of an attribute come from the same domain level in the hierarchy. For example, all values in Birth date are in years, or all are in both months and years. One advantage is that an anonymous view has uniform domains but it may lose more information.

            |  Job | Birth | Postcode | Illness |
            |:----:|:-----:|:--------:|:-------:|
            | cat1 |  1975 |   4350   |   HIV   |
            | cat1 |  1955 |   4350   |   HIV   |
            | cat1 |  1955 |   5432   |   flu   |
            | cat1 |  1955 |   5432   |  fever  |
            | cat2 |  1975 |   4350   |   flu   |
            | cat2 |  1975 |   4350   |  fever  |

            | Job | Birth | Postcode | Illness |
            |:---:|:-----:|:--------:|:-------:|
            |  *  |   *   |   4350   |   HIV   |
            |  *  |   *   |   4350   |   HIV   |
            |  *  |   *   |   5432   |   flu   |
            |  *  |   *   |   5432   |  fever  |
            |  *  |   *   |   4350   |   flu   |
            |  *  |   *   |   4350   |  fever  |
    - **Local recoding**: Values may be generalized to different levels in the domain. In fact one can say that local recoding is a more general model and global recoding is a special case of local recoding. Note that, in the example, known values are replaced by unknown values (*). This is called suppression, which is one special case of generalization, which is in turn one of the ways of recoding.

            |  Job | Birth | Postcode | Illness |
            |:----:|:-----:|:--------:|:-------:|
            | cat1 |  1975 |   4350   |   HIV   |
            | cat1 |  1955 |   4350   |   HIV   |
            | cat1 |  1955 |   5432   |   flu   |
            | cat1 |  1955 |   5432   |  fever  |
            | cat2 |  1975 |   4350   |   flu   |
            | cat2 |  1975 |   4350   |  fever  |

            |  Job | Birth | Postcode | Illness |
            |:----:|:-----:|:--------:|:-------:|
            | cat1 |   *   |   4350   |   HIV   |
            | cat1 |   *   |   4350   |   HIV   |
            | cat1 |  1955 |   5432   |   flu   |
            | cat1 |  1955 |   5432   |  fever  |
            | cat2 |  1975 |   4350   |   flu   |
            | cat2 |  1975 |   4350   |  fever  |

     - Table 2 doesn't protect two patients’ sensitive information, HIV infection. We may not be able to distinguish the two individuals for the first two tuples, but we can derive the fact that both of them are HIV infectious. Suppose one of them is the mayor, we can then confirm that the mayor has contracted HIV. Surely, this is an undesirable outcome. Since (***,1975,4350) is linked to multiple diseases (i.e. HIV and fever) and ('*', '*', 4350) is also linked to multiple diseases (i.e. HIV and flu), it protects individual identifications and hides the implication.

            |  Job | Birth | Postcode | Illness |
            |:----:|:-----:|:--------:|:-------:|
            |   *  |  1975 |   4350   |   HIV   |
            |   *  |   *   |   4350   |   HIV   |
            | cat1 |  1955 |   5432   |   flu   |
            | cat1 |  1955 |   5432   |  fever  |
            |   *  |   *   |   4350   |   flu   |
            |   *  |  1975 |   4350   |  fever  |
- There are two goals for privacy preservation: (1) to protect individual identifications and (2) to protect sensitive relationships. Our focus in this paper is to build a model to protect both in a disclosed data set.
- We propose an (α, k)-anonymity model, where **α is a fraction and k is an integer**. In addition to k-anonymity, we require that, after anonymization, in any equivalence class, the frequency (in fraction) of a sensitive value is no more than α.

### State of the Art
- k-anonymity algorithm Incognito, as the algorithm is not scalable to the size of quasi-identifier and may give a lot of distortions to the data since it is global-recoding based.
- Association rules hiding in a transactional data set, where the rules to be hidden have to be known beforehand and each time only one rule can be hidden. Also, the implementation assumes that frequent itemsets of rules are disjoint.
- Template-based privacy preservation in classification problems, which considers hiding strong associations between some attributes and sensitive classes and combines k-anonymity with association hiding.
- The (c, l)-diversity model is proposed to solve the above problem, which is called the homogeneity attack. However, the (c, l)-diversity model also aims at countering another kind of attack, which is assuming that the attacker has background knowledge to rule out some possible values in a sensitive attribute for the targeted victim. Parameter l describes the level of diversity of sensitive values. If l is larger, there will be more different sensitive values in a group.

### Proposed Algorithm
- Background knowledge attack it's not focused on the paper and should be handled by more special treatment and not by a general anonymization mechanism.
- The model extends the k-anonymity model to the (α, k)-anonymity model to limit the confidence of the implications from the quasi-identifier to a sensitive value (attribute) to within α in order to protect the sensitive information from being inferred by strong implications. We prove that the optimal (α, k)-anonymity by local recoding is NP-hard.
- We also propose a local-recoding algorithm, which is scalable and generate less distortion. In our experiment, we show that, on average, the local-recoding based algorithm performs about 4 times faster and gives about 3 times less distortions of the data set compared with the extended Incognito algorithm. We also describe how the model can be extended to more general cases.

## Problem definition
To start with, it's assumed only one sensitive value, such as HIV. We introduce the **α-deassociation** requirement for the protection.

- DEFINITION 1 (α-DEASSOCIATION REQUIREMENT): Given a data set D, an attribute set Q and a sensitive value s in the domain of attribute S 6∈ Q. Let (E, s) be the set of tuples in equivalence class E containing s for S and α be a user-specified threshold, where 0 < α < 1. Data set D is α-deassociated with respect to attribute set Q and the sensitive value s if the relative frequency of s in every equivalence class is less than or equal to α. That is, |(E, s)|/|E| ≤ α for all equivalence classes E.
- DEFINITION 2 (α, k)-ANONYMIZATION: The **objective** is therefore to **anonymize** a data set so that it **satisfies both the k-anonymity and the α-deassociation criteria**.
    - Both parameters α and k are intuitive and operable in real-world applications. Parameter **α caps the confidence of implications from values in the quasi-identifier to the sensitive value** while parameter **k specifies the minimum number of identical quasi-identifications**.
- DEFINITION 3 (LOCAL RECODING ). Given a data set D of tuples, a function c that convert each tuple t in D to c(t) is a local recoding for D.
    - Local recoding typically distorts the values in the tuples in a data set. We can define a measurement for the amount of distortion generated by a recoding, which we shall call the recoding cost. If a suppression is used for recoding of a value which modifies the value to an unknown *, then the cost can be measured by the total number of suppressions, or the number of *’s in the resulting data set. Our objective is to **find local recoding with a minimum cost**.
- **(α, k)-ANONYMIZATION**: Given a data set D with a quasi-identifier Q and a sensitive value s, is there a local recoding for D by a function c such that, after recoding, (α, k)-anonymity is satisfied and the cost of the recoding is at most C?
- Optimal k-anonymization by local recoding is NP-hard as discussed in [9, 1]. Now, we show that optimal (α, k)-anonymization by local recoding is also NP-hard.

...

# Anonymization in the Time of Big Data
Josep Domingo-Ferrer and Jordi Soria-Comas

## Abstract
Viability of anonymization. Paper focus on k-anonymity, which is the best-known privacy model based on
anonymization. Two main challenges were identified: first, confidential attributes can also e quasi-identifier attributes and may lead to large information loss. Second, in big data there is an unlimited number of data controllers, who may publish independent k-anonymous releases on overlapping populations of subjects.

## Introduction
- **Statistical disclosure control (SDC)** _modifies_ the original data with the aim of protect the privacy of the subjects while preserving sufficient utility for statistical analyses.
- Among the **SDC** methods used, **anonymization** is of particular relevance. This method sets a blur relation between each record and the corresponding subject.
    - Divides attributes into: **quasi-identifier** attributes (QI) and **confidential** attributes.
    - Confidential attributes are those that contain the **sensitive information whose disclosure we want to prevent**. An attribute is classified as a quasi-identifier attribute if **it can help re-identify the subject corresponding to a record** (link the record to a specific subject). The usual quasi-identifier attributes are s**ocio-demographic attributes** such as **age, sex, gender, ZIP code**, etc.
    - > The idea underlying anonymization is to alter the values of quasi-identifier attributes in the data set in order to prevent linkage of its records to subjects. The ultimate goal is to prevent observers from learning the confidential attribute values of identified subjects.
    - Many data protection regulations [2, 3, 1] are built around anonymization

## Background
Covers anonymization concepts, data protection regulations, k-anonymity and some shortcomings of k-anonymity.

### Anonymization
Process of masking the correspondence between records in a data set and the subjects to whom they correspond:
    - **De-identificaiton**: Consists in the suppressing the identifier attributes (those that unambiguously identify a subject). eg: name, social security number, email address, etc.
    - **Quasi-identifier masking**: Quasi-identifier attributes can also be used to reidentify the subject to whom a record corresponds. _However, unlike identifiers, quasi-identifier attributes should not be removed in general, because of the analytical value they convey_.

### Data Protection Regulations and anonymization
The general view of data protection regulations is that anonymized data are not personal (re-identifiable) anymore.
- U.S. Health Insurance Portability and Accountability Act (HIPAA)
- E.U. General Data Protection Regulation (GDPR)

### _k_-Anonymity
- k-Anonymity seeks to guarantee at least a certain level of anonymity for the records in a data set. To that end, k-anonymity assumes that the attributes an observer can use to re-identify a record can be determined beforehand by the data controller, and makes each record indistinguishable with regard to these attributes within a group of k records.
- The term quasi-identifier refers to a set of attributes whose combined values can lead to record re-identification.
- >This is similar to the above-mentioned notion of quasi-identifier attribute but it is not equivalent. The attributes that form a quasi-identifier are quasi-identifier attributes, but a quasi-identifier attribute alone is not necessarily a quasi-identifier.
- To prevent re-identification of records based on a quasi-identifier, k-anonymity **requires each combination of values of the quasi-identifier attributes** to be **shared** by k or more records. In a k-anonymous data set, each group of k or more records sharing the values of all quasi-identifier attributes is called a k-anonymous class.

### Shortcomings _k_-Anonymity


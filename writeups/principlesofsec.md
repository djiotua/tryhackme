# Principles of Security

Learn the principles of information security that secures data and protects systems from abuse.

---

# Task 1 - Introduction

The following room is going to outline some of the fundamental principles of information security. The frameworks used to protect data and systems to the elements of what exactly makes data secure.

The measures, frameworks and protocols discussed throughout this room all play a small part in "Defence in Depth".

_Defence in Depth_ is the use of multiple varied layers of security to an organisation's systems and data in the hopes that multiple layers will provide redundancy in an organisation's security perimeter.

---

_1. Let's proceed!_

No answer needed.

---

# Task 2 - The CIA Triad

The CIA triad is an information security model that is used in consideration throughout creating a security policy. This model has an extensive background, ranging from being used in 1998.

This history is because the security of information (information security) does not start and/or end with cybersecurity, but instead, applies to scenarios like filing, record storage, etc.

Consisting of three sections: _Confidentiality_, _Integrity_ and _Availability_ (_CIA_), this model has quickly become an industry standard today. This model should help determine the value of data that it applies to, and in turn, the attention it needs from the business.

![cia_triad](https://github.com/djiotua/tryhackme/assets/134016731/d0a321db-8791-41da-a91c-e5a991a5102c)

The CIA triad is unlike a traditional model where you have individual sections; instead, it is a continuous cycle. Whilst the three elements to the CIA triad can arguably overlap, if even just one element is not met, then the other two are rendered useless (similar to the fire triangle). If a security policy does not answer these three sections, it is seldom an effective security policy.

Whilst the three elements to the CIA triad are arguably self-explanatory, let's explore these and contextualise them into cybersecurity.

![2092d19d7d7e9eaecead2baca007a406](https://github.com/djiotua/tryhackme/assets/134016731/991cd06d-b5ad-449f-bbe7-9487b8c3f77f)

### Confidentiality

This element is the protection of data from unauthorized access and misuse. Organisations will always have some form of sensitive data stored on their systems. To provide confidentiality is to protect this data from parties that it is not intended for.

There are many real-world examples for this, for example, employee records and accounting documents will be considered sensitive. Confidentiality will be provided in the sense that only HR administrators will access employee records, where vetting and tight access controls are in place. Accounting records are less valuable (and therefore less sensitive), so not as stringent access controls would be in place for these documents. Or, for example, governments using a sensitivity classification rating system (top-secret, classified, unclassified).

![8baaae53303b90143e5cb20821202bd4](https://github.com/djiotua/tryhackme/assets/134016731/15bfc95a-4aee-400a-9b02-e1f0236a2155)

### Integrity

The CIA triad element of integrity is the condition where information is kept accurate and consistent unless authorized changes are made. It is possible for the information to change because of careless access and use, errors in the information system, or unauthorized access and use. In the CIA triad, integrity is maintained when the information remains unchanged during storage, transmission, and usage not involving modification to the information. Steps must be taken to ensure data cannot be altered by unauthorised people (for example, in a breach of confidentiality).

Many defences to ensure integrity can be put in place. Access control and rigorous authentication can help prevent authorized users from making unauthorized changes. Hash verifications and digital signatures can help ensure that transactions are authentic and that files have not been modified or corrupted.

![d194e35fc5fd158b20e64a3c8c5123d1](https://github.com/djiotua/tryhackme/assets/134016731/8d457f47-1d4c-44cd-ba29-5cc2accaad75)

### Availability

In order for data to be useful, it must be available and accessible by the user.

The main concern in the CIA triad is that the information should be available when authorised users need to access it.

Availability is very often a key benchmark for an organisation. For example, having 99.99% uptime on their websites or systems (this is laid out in Service Level Agreements). When a system is unavailable, it often results in damage to an organisations reputation and loss of finances. Availability is achieved through a combination of many elements, including:

- Having reliable and well-tested hardware for their information technology servers (i.e. reputable servers)
- Having redundant technology and services in the case of failure of the primary
- Implementing well-versed security protocols to protect technology and services from attack

---

_1. What element of the CIA triad ensures that data cannot be altered by unauthorised people?_

  <details>
    <summary>Answer</summary>

    Integrity
  </details>

  

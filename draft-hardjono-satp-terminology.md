---

stand_alone: yes
pi:
  rfcedstyle: yes
  toc: yes
  tocindent: yes
  tocdepth: 4
  sortrefs: yes
  symrefs: yes
  strict: yes
  comments: yes
  inline: yes
  text-list-symbols: o-*+
  compact: yes
  subcompact: no

title: Secure Asset Transfer Protocol (SATP) Core
abbrev: SATP Core
docname: draft-ietf-satp-core-latest
category: info

ipr: trust200902
area: "Applications and Real-Time"
workgroup: "Secure Asset Transfer Protocol"

stream: IETF
keyword: Internet-Draft
consensus: true

venue:
  group: "Secure Asset Transfer Protocol"
  type: "Working Group"
  mail: "sat@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/sat/"
  github: "ietf-satp/draft-ietf-satp-core"
  latest: "https://ietf-satp.github.io/draft-ietf-satp-core/draft-ietf-satp-core.html"

author:

  -
    ins: T. Hardjono
    name: Thomas Hardjono
    organization: MIT
    email: hardjono@mit.edu
  -
    ins: V. Ramakrishna
    name: Venkatraman Ramakrishna
    organization: IBM
    email: vramakr2@in.ibm.com

    
informative:
  NIST:
    author:
    - ins: D. Yaga
    - ins: P. Mell
    - ins: N. Roby
    - ins: K. Scarfone
    date: October 2018
    target: https://doi.org/10.6028/NIST.IR.8202
    title: NIST Blockchain Technology Overview (NISTR-8202)

  ECDSA:
    author:
    date: February 2023
    target: https://doi.org/10.6028/NIST.FIPS.186-5
    title: Digital Signature Standard (FIPS 186-5)
    
  MICA:
    author:
    - ins: European Commission
    date: June 2023
    target: https://www.esma.europa.eu/esmas-activities/digital-finance-and-innovation/markets-crypto-assets-regulation-mica
    title: EU Directive on Markets in Crypto-Assets Regulation (MiCA)

  ARCH:
    author:
    - ins: T. Hardjono
    - ins: M. Hargreaves
    - ins: N. Smith
    - ins: V. Ramakrishna
    date: June 2024
    target: https://datatracker.ietf.org/doc/draft-ietf-satp-architecture/
    title: Secure Asset Transfer (SAT) Interoperability Architecture

  RFC5939:
    author:
    - ins: F. Andreasen
    date: September 2010
    target: https://www.rfc-editor.org/info/rfc5939
    title: Session Description Protocol (SDP) Capability Negotiation

  RFC9334:
    author:
    - ins: H. Birkholz
    - ins: D. Thaler
    - ins: M. Richardson
    - ins: N. Smith
    - ins: W. Pan
    date: January 2023
    target: https://www.rfc-editor.org/info/rfc9334
    title: Remote Attestation Procedures Architecture (RATS)

normative:
  JWT: RFC7519
  JSON: RFC8259
  JWS: RFC7515
  REQ-LEVEL: RFC2119

--- abstract

This memo collates existing terminology related to digital assets, asset networks and distributed ledger technology (DLT) that are relevant to the secure asset transfer protocol (SATP) and the IETF more broadly. Existing terms are borrowed as much as possible, and new terms are introduced only when necessary and with emphasis on technology neutrality.

--- middle

# Introduction

{: #introduction-doc}

This memo collates existing terminology related to digital assets, asset networks and distributed ledger technology (DLT) that are relevant to the secure asset transfer protocol (SATP) and the IETF more broadly. Existing terms are borrowed as much as possible, and new terms are introduced only when necessary and with emphasis on technology neutrality.



# Conventions used in this document

{: #conventions}

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL"
in this document are to be interpreted as described in RFC 2119 {{REQ-LEVEL}}.

In this document, these words will appear with that interpretation
only when in ALL CAPS. Lower case uses of these words are not to be
interpreted as carrying significance described in RFC 2119.

# Terminology

{: #terminology-doc}

The following are some terminology used in the current document, some borrowed from {{NIST}}:

- Digital asset: digital representation of a value or of a right that is able to be
  transferred and stored electronically using distributed ledger technology or similar technology {{MICA}}.

- Asset network: A monolithic system or a set of distributed systems that manage digital assets.

- Client application: This is the application employed by a user
  to interact with a gateway.

- Gateway: The computer system functionally capable of acting
  as a gateway in an asset transfer.

- Sender gateway: The gateway that initiates a unidirectional asset transfer.

- Recipient gateway: The gateway that is the recipient side of
  a unidirectional asset transfer.

- Claim: An assertion made by an Entity {{JWT}}.

- Claim Type: Syntax used for representing a Claim Value {{JWT}}.

- Gateway Claim: An assertion made by a Gateway regarding the status or
  condition of resources (e.g. assets, public keys, etc.)
  accessible to that gateway (e.g. within its asset network or system).

In the remainder of this document, for brevity of description the term “asset network” will often be shorted to "network".


```
                 +----------+                +----------+
                 |  Client  |                | Off-net  |
          ------ |   (App)  |                | Resource |
          |      +----------+                +----------+
          |           |                      |   API3   |
          |           |                      +----------+
          |           |                           ^
          |           V                           |
          |      +---------+                      |
          V      |   API1  |                      |
       +-----+   +---------+----+        +----+---------+   +-----+
       |     |   |         |    |        |    |         |   |     |
       | Net.|   | Gateway |API2|        |API2| Gateway |   | Net.|
       | NW1 |---|    G1   |    |<------>|    |    G2   |---| NW2 |
       |     |   |         |    |        |    |         |   |     |
       +-----+   +---------+----+        +----+---------+   +-----+
                               Figure 1
```


# Acknowledgements

{: #satp-core-contributors}

The authors would like to thank the following people for their input and support:

Andre Augusto,
Denis Avrilionis,
Rafael Belchior,
Alexandru Chiriac,
Anthony Culligan,
Claire Facer,
Martin Gfeller,
Wes Hardaker,
David Millman,
Krishnasuri Narayanam,
Anais Ofranc,
Luke Riley,
John Robotham,
Orie Steele,
Yaron Scheffer,
Peter Somogyvari,
Weijia Zhang.


--- back



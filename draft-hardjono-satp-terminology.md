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

title: Secure Asset Transfer Protocol (SATP) Terminology
abbrev: SATP Terminology
docname: draft-hardjono-satp-terminology-latest
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
  github: "ietf-satp/draft-hardjono-satp-terminology"
  latest: "https://ietf-satp.github.io/draft-hardjono-satp-terminology/draft-hardjono-satp-terminology.html"

author:

  -
    ins: M. Hargreaves
    name: Martin Hargreaves
    organization: Quant Network
    email: martin.hargreaves@quant.network
  -
    ins: T. Hardjono
    name: Thomas Hardjono
    organization: MIT
    email: hardjono@mit.edu
  -
    ins: R. Belchior
    name: Rafael Belchior
    organization: INESC-ID, Técnico Lisboa, Blockdaemon
    email: rafael.belchior@tecnico.ulisboa.pt
  -
    ins: V. Ramakrishna
    name: Venkatraman Ramakrishna
    organization: IBM
    email: vramakr2@in.ibm.com
  -
    ins: A. Chiriac
    name: Alex Chiriac
    organization: Quant Network
    email: alexandru.chiriac@quant.network

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

  RFC5939: RFC5939

  RFC9334: RFC9334

normative:
  JWT: RFC7519
  JSON: RFC8259
  JWS: RFC7515
  JWA: RFC7518
  REQ-LEVEL: RFC2119
  BASE64: RFC4648
  DATETIME: RFC3339
  RFC2616: RFC2616

  X.500:
    author:
    - ins: ITU-T
    date: 2005
    title: "The Directory: Overview of concepts, models and services"

--- abstract

This memo collates existing terminology related to digital assets, asset networks and distributed ledger technology (DLT) that are relevant to the secure asset transfer protocol (SATP) and the IETF more broadly. Existing terms are borrowed as much as possible, and new terms are introduced only when necessary and with emphasis on technology neutrality.

--- middle

# Introduction
{: #introduction}
The SAT protocol for interoperability utilizes peered gateways to perform a unidirectional transfer of a digital assets, from an origin asset network to a destination asset network [ARCH].  As stated in [CORE] the SAT protocol is agnostic to the type of network or system behind the gateways, and the protocol focuses on the interactions between the two gateways.

While the SAT protocol defines the interaction between two gateways such that certain properties of the transfer is achieved (atomicity, consistency, isolation, durability), the protocol specification does not define how each gateway interfaces and interacts with their respective asset network. Furthermore, the SAT protocol employs an abstraction of the functions present in these asset network.  Examples of such abstraction include the functions of locking (disabling) the asset on a network, burning (destroying) an asset, minting (creating) and so on. However, in order to achieve a higher degree of precision in describing the utilization of the SAT protocol and its impact on asset networks, a definition of these terms is required.

The goal of this document is to provide a terminology definition of the entities, constructs and on-chain functions that are relevant within the context of a SAT protocol deployment with gateways. A layered approach is adopted to describe these constructs and on-chain  functions, in order to minimize confusion with regards to which entities are utilizing these.

As far as possible, this document will borrow existing terminology from other published standards. The sources of this existing terminology will be cited. When needed, the document will be verbose in providing definitions in order to remove any ambiguity in the use of the constructs (e.g. smart contract invoked by a gateway, versus that invoked by a client).

# Asset Networks Related Terminology
{: #terms1}

* Address: A short, alphanumeric string derived from a user’s public key using a hash function, with additional data to detect errors. Addresses are used to send and receive digital assets. [NISTIR8202]
Account: An entity in a blockchain that is identified with an address and can send transactions to the blockchain. [NISTIR8301]
Atomic swap: An exchange of tokens that does not involve the intervention of any trusted intermediary and automatically reverts if all of the provisions are not met. [NISTIR8301]

* Blockchain: Blockchains are distributed digital ledgers of cryptographically signed transactions that are grouped into blocks. Each block is cryptographically linked to the previous one (making it tamper evident) after validation and undergoing a consensus decision. As new blocks are added, older blocks become more difficult to modify (creating tamper resistance). New blocks are replicated across copies of the ledger within the network, and any conflicts are resolved automatically using established rules. [NISTIR8202]

* Custodian: A third-party entity that holds and safeguards a user’s private keys or digital assets on their behalf. Depending on the system, a custodian may act as an exchange and provide additional services, such as staking, lending, account recovery, or security features. [NISTIR8301]

* Consensus: A process to achieve agreement within a distributed system on the valid Cryptocurrency state. Also known as a consensus algorithm, consensus mechanism, consensus method. [NISTIR8202]

* Double Spend: Transacting with the same set of digital assets more than once. [NISTIR8202]


* Off-chain: Refers to data that is stored or a process that is implemented and executed outside of any blockchain system. [NISTIR8301]

* Oracle: A source of data from outside a blockchain that serves as input for a smart contract. [NISTIR8301]

* Permissioned blockchain: A system where every node, and every user must be granted permissions to utilize the system (generally assigned by an administrator or consortium). [NISTIR8202]

* Permissionless blockchain: A system where all users’ permissions are equal and not set by any administrator or consortium. [NISTIR8202]

* Smart contract: A collection of code and data (sometimes referred to as functions and state) that is deployed using cryptographically signed transactions on the blockchain network. The smart contract is executed by nodes within the blockchain network; all nodes must derive the same results for the execution, and the results of execution are recorded on the blockchain. [NISTIR8202]

* Wallet: Software used to store and manage asymmetric-keys and addresses used for transactions. [NISTIR8202]

* Wallets, Custodial: Account custody -- and the custody of the associated tokens--  which is delegated to institutional third-party custodians who hold and safeguard private keys on behalf of users. They provide different degrees of custody services and risk management. Custodial wallets are also known as externally hosted wallets or managed wallets. [NISTIR8301]


{::boilerplate bcp14-tagged}

# Assumptions and Principles
{: #assumptions}

The following assumptions and principles underlie the design of the
      current gateway architecture, and correspond
      to the design principles of the Internet architecture.


## Design Principles
{: #designprinciples}

* Opaque network resources:
The interior resources of each network are assumed
to be opaque to (hidden from) external entities.
Any resources to be made accessible to an external entity
must be made explicitly accessible by a gateway with proper authorization.

* Externalization of value:
The asset transfer protocol is agnostic (oblivious)
to the economic or monetary value (if any) of the digital asset being transferred.

The opaque resources principle permits the architecture
to be applied in cases where one (or both) networks are private (closed membership).
It is the analog of the autonomous systems principle in IP networking [Clar88],
where interior routes in local subnets are not visible to other external networks.

The value-externalization principle permits an asset transfer protocol
to be designed for efficiency, security and reliability --
independent of the changes in the perceived economic value of the digital asset.
It is the analog of the end-to-end principle in the Internet architecture [SRC84],
where contextual information is placed at the endpoints of the transfer.

## Operational Assumptions
{: #operationalassumptions}
The following conditions are assumed to have occurred,
leading to the invocation of the asset transfer protocol between two gateways:

* Application level context establishment: The transfer request from an
      Originator utilizing an application (App1) in the origin network is assumed
      to have occurred, and that some context-identifier has subsequently been derived
      by the respective applications (App1 and App2).
      Furthermore, this context-identifier is assumed to have been delivered
      by the each application to its corresponding gateway,
      permiting each gateway to internally bind the
      transfer session-identifier to that context-identifier.

 * Identification of asset to be transferred: The applications at
the originator and the beneficiary are assumed to have identified
the digital asset to be transferred.

 * Identification of originator and beneficiary:
The originator and beneficiary are assumed to have been
identified and that consent has been obtained from
both parties regarding the asset transfer.

 * Identification of origin and destination asset networks:
The origin and destination networks are assumed to have been identified.

 * Selection of gateway: The two corresponding gateways
at the origin and destination networks are assumed to have been identified and selected.


## Assumptions Regarding Gateway Operators
{: #operatorassumptions}
The following conditions are assumed to have occurred,
leading to the invocation of the asset transfer protocol
between two gateways:


 * Identification of gateway-owners:
The owners of the two corresponding gateways are assumed
to have been identified and their ownership status verified.


 * Gateway liabilities: Gateways and gateway-operators are assumed
to take on legal and financial liability for their transactions,
and gateways are assumed to operate under
a well-defined legal framework (e.g. contractual relationship).
Furthermore, the legal framework is assumed to be supported by
compatible legislation in the relevant jurisdictions
where the gateways are operating.

 * Gateway message signatures: All messages between gateways
are assumed to be signed and verified (e.g. X.509).

 * Transitory ownership of asset by gateway:
Assets being transferred via SAT will technically be owned
by gateway in transit and gateways are liable for
them while they have ownership.

* Network data: Gateways are assumed to have mechanisms in place to trust data
returned from their local networks.
This will depend on the technical architecture and capabilities
of each specific network.

 * Gateways are trusted: The gateways are assumed to be trusted
to carry-out all the stages of the protocol described in this architecture.


# Gateway Interoperability Modes
{: #modes}

The current interoperability architecture based
on gateways recognizes several types of transfer flows:

* Asset transfer: This refers to the transfer of a digital asset
from the origin network to a destination network,
where a successful asset transfer causes the asset
to be extinguished in the origin network and be created (generated)
at the destination network.

 * Data sharing: This refers to the sharing of data only under authorization,
in such a way that the data can be verified by a third party.
The data sharing mode addresses the use-cases where
the state update in one network or system depends on the existence of state information
recorded in a different network or system.

 * Asset exchange (swap): This refers to the case where
two users are present in two networks,
and they perform concurrent and atomic swaps of two assets
in the two corresponding networks,
without transferring the assets outside the networks.
The gateways aid in coordinating the messages pertaining to the swap.

The remainder of this architecture document will focus on the asset transfer flows.

# Architecture
{: #architecture}

## Goal of Architecture
{: #goalarchitecture}

The goal of the interoperability architecture is to permit two (2) gateways
belonging to distinct networks to conduct a transfer of digital assets transfer between them,
in a secure, atomic and verifiable manner.


The asset as understood by the two gateways is expressed
in an standard digital format in a way meaningful
to the gateway syntactically and semantically.


The architecture recognizes that there are different networks currently
in operation and evolving, and that in many cases the interior technical constructs
in these networks maybe incompatible with one another.


The architecture therefore assumes that in addition
to implementing the bilateral secure asset transfer protocol,
a gateway has the role of making opaque (i.e. hiding)
the constructs that are local and specific to its network.


Overall this approach ensures a high degree of interoperability across these networks,
where each network can operate as a true autonomous system.
Additionally, this approach permits each network to evolve
its interior technology implementations without affecting other (external) networks.

The current architecture focuses on unidirectional asset transfers,
although the building blocks in this architecture can be used
to support protocols for bidirectional transfers.

For simplicity the current architecture employs two (2) gateways
per transfer as the basic building block,
with one gateway in the origin and destination networks respectively.
However, the architecture seeks to be extensible to address future cases
involving multiple gateways at both sides.

## Overview of Asset Transfer
{: #overviewtransfer}

An asset transfer between two networks is performed using
a secure asset transfer protocol implemented by
the gateways in the respective networks.
The two gateways implement the protocol in a direct interaction (unmediated).

A successful transfer results in the asset being extinguished (burned)
or marked on the origin network, and for the asset to be regenerated (minted)
at the destination network.

The secure asset transfer protocol provides a coordination
between the two gateways through the various message flows
in the protocol that is communicated over a secure channel.

The protocol implements a commitment mechanism between the
two gateways to ensure that the relevant properties
atomicity, consistency, isolation, and durability are achieved in the transfer.

The mechanism to extinguish (burn) or regenerate (mint) an asset from/into
a network by its gateway is dependent on the specific network
and is outside the scope of the current architecture.

As part of the commitment mechanism,
the sender gateway in the origin network must deliver a signed assertion
to the receiver gateway at the destination network which states that asset
in question has been extinguished (burned) from the origin network.

Similarly, the receiver gateway at the destination network
must in return deliver a signed assertion to the sender gateway at the origin network
which states that the asset has been regenerated (minted) in the destination network.

These two tasks must be performed in a synchronized fashion
between the two gateways,
and the commitment mechanism must provide sufficent evidence of the
asset transfer that is verifiable by an authorized third party.

## Desirable Properties of Asset Transfer
{: #properties}
The desirable features of asset transfers
between two gateway  include, but not limited,
to the following:

* Atomicity: A transfer must either commit or entirely fail (failure means no change to asset state).

* Consistency: A transfer (commit or fail) always leaves the networks in a consistent state
(i.e. the asset is located in one network only at any time).

* Isolation: While the transfer is occurring, the asset state cannot be modified in the origin network.

* Durability: Once a transfer has been committed by both gateways,
it must remain so regardless of subsequent gateway crashes.


* Verifiable by authorized third parties:
The proof that the asset has been extinguished in the origin network,
and the proof that the asset has been generated
in the destination network must be verifiable by an authorized third party.


An implementation of the asset transfer protocol should satisfy these properties,
independent of whether the implementation employs
stateful messaging or stateless messaging between the two gateways.

Effecting an asset transfer safely and securely is not simply
a matter of communicating desire or intent between two systems represented
by gateways, though such communication is a necessary part of asset transfer.
The systems, or at least their gateway proxies,
must be interoperable in order to transfer assets among themselves,
but such interoperability imposes strictly more demands on systems managing digital assets,
especially systems that are built on distributed ledgers,
than conventional communication interoperability does.

Communication interoperability, which is concerned with syntax and semantics of information
geared towards producing a common understanding (or knowledge reconciliation) among systems,
is insufficient to fulfill an asset transfer that requires systems to carry out state
updates in concert with each other.
But communication, or messaging standards, play a necessary and complementary role
to asset transfer protocols.
An exemplar of this is ISO 20022,
which is a comprehensive global standard for financial messaging that
specifies message syntax for common actions occurring in financial business processes,
including payments, credit card transactions, securities settlements, funds, and trade [ISO20022].
This standard provides the tools to model business processes from basic logical building blocks
and schemas to construct messages using common formats like XML, JSON, and ASN.1.

As we will see later in this document, such messaging standards are useful to
communicate information about the states of processes and digital assets across systems,
to make requests, and to convey intent.
They therefore play a necessary and complementary role in asset transfer protocols.
However they are by themselves insufficient to ensure the ACID and verifiability properties described earlier.
Another way to think about the relationship between messaging standards
like ISO 20022 and asset transfer protocols is that the former is concerned
with the "what" of cross-system interoperability whereas
the latter is concerned with the "how".
Both kinds of protocols treat systems as black boxes,
but asset transfer protocols must place some responsibility,
and depend, on systems to drive a protocol instance to successful conclusion.


## Event log-data, crash recovery and backup gateways
{: #log-data}

Implementations of a gateway should maintain event logs and checkpoints
for the purpose of gateway crash recovery.
The log-data generated by a gateway should be considered as
an interior resource accessible to other authorized gateways within the same network.

The mechanism used to provide gateway crash-recovery is dependent
on the specific network.
For interoperability purposes the information contained in the log and
the format of the log-data should be standardized.

The resumption of an interrupted transfer session (e.g. due to gateway crash, network failure, etc.)
should take into consideration the aspects of secure channel establishment
and the aspects of the transfer protocol resumption.
In some cases, a new secure channel (e.g. TLS session) may need to be
established between the two gateways, before a resumption of the transfer can begin.

The log-data collected by a gateway acts also as
a checkpoint mechanism to assist the recovered (or backup) gateway in continuing the transfer.
The point at which to re-start the transfer protocol flow
is dependent on the implementation of the gateway recovery strategy.


## Overview of the Stages in Asset Transfer
{: #phasetransfer}

The interaction between two gateways in the secure asset transfer protocol is summarized in Figure 1,
where the origin network is NW1 and the destination network is NW2. T
he gateways are denoted as G1 and G2 respectively.

~~~
         Originator                                   Beneficiary
             |                                             |
      +-------------+                               +-------------+
      |   Client    |                               |   Client    |
      | Application |                               | Application |
      |    (App1)   |                               |    (App2)   |
      +-------------+                               +-------------+
             |                                             |
             |                  (Stages)                   |
             V                                             V
      +-------------+       |<-----(1)----->|       +-------------+
      |    Network  |  +----+               +----+  |   Network   |
      |     NW1     |  |Gate|               |Gate|  |     NW2     |
      |             |--|way |<-----(2)----->|way |--|             |
      | +---------+ |  | G1 |               | G2 |  | +---------+ |
      | |  State  | |  +----+               +----+  | |   State | |
      | | Data DB1| |  +----+               +----+  | | Data DB2| |
      | +---------+ |       |<-----(3)----->|       | +---------+ |
      +-------------+                               +-------------+
~~~

{: #gateway-stages}

The stages are summarized as follows.

* Stage 0: Pre-transfer Verification and Context Establishment.
The two applications utilized by the originator and beneficiary
is assumed to interact as part of the asset transfer.
In this stage, the applications App1 and App2 may establish
some shared transfer context information (e.g.  Context-ID) at the application level
that will be made
available to their respective gateways G1 and G2.
The legal verification of the identities of the Originator and
Beneficiary may occur in this stages [FATF].
This stage is outside the scope of the current architecture.

* Stage 1: Transfer Initiation Claims negotiations.
In this stage gateways G1 and G2 must exchange information (claims)
regarding the asset to be transferred, the identity information of
the Originator and Beneficiary and other information
regarding relevant actors (e.g. gateway owner/operator).

Additionally, the gateways must exchange information regarding
the gateway and network characteristics that are unique
to G1, G2, NW1 and NW2 for this particular transfer instance.


* Stage 2: Lock Assertion and Receipt.  In this stage, gateway G1
must provide gateway G2 with a signed assertion that
the asset in NW1 has been immobilized and under the control on G1.
A signed assertion is needed because NW1 may be a private or closed network,
and therefore the state-database (ledger) in NW1 is no readable by external entities including by G2.
Gateway G1 must therefore make this signed assertion explicitly.
Note that the owner/operator of G1 takes on liability in signing this assertion.


* Stage 3: Commitment Preparation and Finalization.
In this stage gateways G1 and G2 commit to the unidirectional asset transfer
using a 3PC (3-phase commit) subprotocol.

These transfer stages will be further discussed below.


# Transfer Initiation Claims negotiations (Stage-1)
{: #phase-one}

The purpose of this stage is for the sender gateway (G1) and
the receiver gateway (G2) to agree on the asset instance
to be transferred from the origin network NW1 to the destination network NW2.
In addition, the gateways must exchange validated information or
artifacts regarding the originator and beneficiary of the asset transfer,
and exchange gateway-specific and network-specific parameters.

These artifacts are contained in the Transfer Initiation Claims set
that is sent from gateway G1 to G2. The set of claims may be
negotiated between GH1 and G2 in multi-round set of messages.



~~~
      App1  DB1          G1                     G2          DB2    App2
       |     |            |                      |            |     |
       |     |            |                      |            |     |
       |<------------ (transfer context establishment) ------------>|
       |     |            |                      |            |     |
       |---request------->|                      |<------request----|
       |     |            |                      |            |     |
     ..|.....|............|......................|............|.....|..
       |     |            |       Stage 1        |            |     |
       |     |            |                      |            |     |
       |     |       (1.1)|<---Proposal Claims-->|            |     |
       |     |            |                      |            |     |
       |     |            |                      |            |     |
       |     |       (1.2)|<--Proposal Receipt-->|            |     |
       |     |            |                      |            |     |
       |     |            |                      |            |     |
       |     |       (1.3)|<--Transf. Commence-->|            |     |
       |     |            |                      |            |     |
       |     |            |                      |            |     |
       |     |       (1.4)|<--- ACK Commence --->|            |     |
       |     |            |                      |            |     |
     ..|.....|............|......................|............|.....|..
       |     |            |                      |            |     |

~~~
{: #phaseone-figure}


This stage starts with the assumption that in network NW1 the gateway
who processes the asset transfer has been selected (namely gateway G1).
It also assumes that the destination network NW2 has been identified
where the beneficiary is located, and that gateway G2 in
network NW2 has been identified.

The first message (Transfer Proposal Claims) maybe multi-round in
the sense there is a negotiation of the claims between G1 and G2.
Once G2 accepts the agreed claims,
G2 must send a signed receipt carrying the hash of the claims agreed.


There are several steps that may occur in Stage 1:

* Secure channel establishment between G1 and G2:
This includes the mutual verification of the gateway device identities
and the exchange of the relevant parameters for secure channel establishment.
In cases where device attestation [^1] is required,
the mutual attestation protocol must occur
between G1 and G2 prior to proceeding to the next stage.

[^1]: Add ref to RATS document

* Mutual device attestations: In cases where device attestation
is required, each gateway must yield attestation evidence
to the other regarding its configuration.
A gateway may take on the role as a attestation verifier,
or it may rely on an external verifier to appraise the received evidence.

* Validation of the gateway ownership:
There must be a means for gateway G1 and G2 to verify their respective ownerships
(i.e. entities owning G1 and G2 respectively).
Examples of ownership verification mechanism include X.509 certificates,
directories of gateways and owners, and others.

* Validation of owner status: In some jurisdictions,
limitations may be placed for regulated asset service providers
to transact only with other similarly regulated service providers.
Examples of mechanisms used to validate legal status of service providers
include directories, Extended Validation (EV) X.509 certificates, and others.

* Identification and validation of type/asset profile:
Both gateways must agree on the type of asset being
transferred based on the published profile of the asset.
Gateway G1 must communicate the asset-profile identification
to gateway G2, who in turn must validate both the legal status of
the asset as well as the technical capability of its network to accept the type of asset.
The policies governing network NW2 with regards to permissible incoming assets
must be enforced by G2.

* Exchange of Travel Rule information and validation:
In jurisdictions where the Travel Rule policies
regarding originator and beneficiary information is enforced [FATF],
the owners of gateways G1 and G2 must comply to the Travel Rule.
Mechanisms must be used to permit gateways G1 and G2
to make available originator/beneficiary information
to one another in such a away that the Travel Rule information
can be logged as part of the asset transfer history.

* Negotiation of asset transfer protocol parameters:
Gateway G1 and G2 must agree on the parameters to be employed within
the asset transfer protocol.
Examples include endpoints definitions for resources,
type of commitment flows (e.g. 2PC or 3PC),
lock-time durations, and others [SAT].

We do not need to invent new standards for several of these steps.
Instead, we can rely on existing messaging standards like ISO 20022 [ISO20022]
or ITIN [ITIN] for gateway ownership validation,
owner status validation, asset profile identification, and
communication of travel rule and transfer context information.
For identification of digital assets maintained by
distributed ledgers or blockchain systems,
we can also rely on standards like ITIN [ITIN].

Once gateways G1 and G2 agree on the claims related to the asset transfer,
the two gateways can proceed by G1 sending the Transfer Commence message,
which must be explicitly acknowledged by gateway G2.

# Asset Lock Assertion and Receipt (Stage 2)
{: #phase-two}

In this stage, gateway G1 must issue a signed assertion that
the asset in origin network NW1 has been immobilized and under the control of G1.


The steps of Stage 2 are summarized in Figure 4, and broadly consists of the following:

* G1 lock/escrow asset (2.1): Gateway G1 proceeds to establish
a lock or escrow the asset belonging to the originator.
This prevents other local transactions in NW1 from changing the state of the asset
until such time the lock by G1 is finalized or released.
A time-lock or escrow may also be employed.


* Lock Assertion (2.2): Gateway G1 sends a digitally signed assertion
regarding the locked (escrowed or immobilized) state on the asset in network NW1.
The signature by G1 is performed using its entity public-key pair.
This signature signifies that G1 (i.e. its owner/operator) is legally standing
behind its statement regarding the locked/escrowed state on the asset.
The mechanism to lock or immobilize the asset is outside the scope of SATP.


* G2 Logs and Broadcasts lock-assertion information (2.3): Gateway G2 logs a copy of the signed
      lock-assertion message received in Step 2.4 to its local state data DB2.
      G2 may also broadcast the fasts of the lock-assertion to all members of network NW2.
      The mechanism to log and to broadcast is out of scope for SATP.


* Lock-Assertion Receipt  (2.4): If gateway G2 accepts the signed assertion from G1,
then G2 responds with a digitally signed receipt message
which includes a hash of the previous lock-assertion message.
The signature by G2 is performed using its entity public-key pair.
Otherwise, if G2 declines accepting the assertion then G2 can simply ignore
the transfer and let the session time-out (i.e. transfer attempt has failed).

~~~

        Orig DB1           G1                   G2            DB2  Benef
        |     |            |      (Stage 1)     |              |     |
        |     |            |                    |              |     |
      ..|.....|............|....................|..............|.....|..
        |     |            |       Stage 2      |              |     |
        |     |            |                    |              |     |
        |     |<---Lock----|(2.1)               |              |     |
        |     |            |                    |              |     |
        |     |       (2.2)|--Lock-Assertion--->|              |     |
        |     |            |                    |              |     |
        |     |            |               (2.3)|--Broadcast-->|     |
        |     |            |                    |              |     |
        |     |            |                    |              |     |
        |     |            |<-----Receipt-------|(2.4)         |     |
        |     |            |                    |              |     |
      ..|.....|............|....................|..............|.....|..
        |     |            |                    |              |     |
~~~
{: #phasetwo-figure}


The purpose of the signed lock-assertion is for dispute resolution between G1 and G2
(i.e. the entities who own and operate G1 and G2 respectively)
in the case that asset state inconsistencies in NW1 and NW2 are discovered later.

The gateway G2 must return a digitally signed receipt to G1
regarding the earlier signed lock-assertion in order to
cover G1 (exculpatory proof) in the case of later denial by G2.

# Commitment Preparation and Finalization (Stage 3)
{: #phase-three}

In Stage 3 the gateways G1 and G2 finalizes to the asset transfer
by performing a commitment protocol (e.g. 2PC or 3PC) as a process (sub-protocol)
embedded within the overall SATP asset transfer protocol.

Upon receiving the signed receipt message from G2 in the previous stage,
G1 begins the commitment (see Figure 5):

* Commit-prepare (3.1):
Gateway G1 indicates to G2 to prepare for the commitment of the transfer.
This message must include a hash of the previous messages (message 2.5 and 2.6).

* Temporary asset mint (3.2): Gateway G2 creates (mints)
an equivalent asset in NW2 assigned to itself as the owner.
This step can be reversed (i.e. asset destroyed)
in the case of the failure in the commitment steps
because G2 is still the owner of the asset in NW2.

* Commit-ready (3.3): Gateway G2 sends a commit-ready message
to G1 indicating that it is ready to carry-out the last steps of
the commitment subprotocol.
Note that that the entire asset transfer session can be aborted
before this step without affecting the asset state in the respective networks.

* Asset burn (3.4): Gateway G1 extinguishes (burns) the asset
in network NW1 which it has locked since Step 2.3.

* Commit-final assertion (3.5): Gateway G1 indicates to G2 that G1 has
      performed the extinguishment of the asset in NW1.  This message
      must be digitally signed by G1.

* Asset-assignment (3.6): Gateway G2 assigns the minted asset
(which it has been self-holding since Step 3.2) to the Beneficiary.

* ACK-final receipt (3.7): Gateway G2 sends a signed assertion
that it has assigned the asset to the intended Beneficiary.

* Receipt broadcast (3.8) Gateway G1 logs a copy of the
signed receipt message to its local state data DB2.
G1 may also broadcast the fasts of the signed receipt
to all members of network NW1.
The mechanism to log and to broadcast is out of scope for SATP.

* Transfer complete (3.9): Gateway G1 must explicitly close the
      asset transfer session with gateway G2.  This allows both sides to
      close down the secure channel established earlier in Stage 1.

~~~
        Orig DB1           G1                   G2           DB2  Benef
        |     |             |      (Stage 2)     |            |     |
        |     |             |                    |            |     |
      ..|.....|.............|....................|............|.....|..
        |     |             |       Stage 3      |            |     |
        |     |             |                    |            |     |
        |     |        (3.1)|--Commit Prepare--->|            |     |
        |     |             |                    |            |     |
        |     |             |               (3.2)|----Mint--->|     |
        |     |             |                    |            |     |
        |     |             |<--Commit Ready ----|(3.3)       |     |
        |     |             |                    |            |     |
        |     |             |                    |            |     |
        |     |<---Burn-----|(3.4)               |            |     |
        |     |             |                    |            |     |
        |     |        (3.5)|-Commit Final Asrt->|            |     |
        |     |             |                    |            |     |
        |     |             |                    |            |     |
        |     |             |               (3.6)|---Assign-->|     |
        |     |             |                    |            |     |
        |     |             |<-----ACK Final-----|(3.7)       |     |
        |     |             |                    |            |     |
        |     |             |                    |            |     |
        |     |<-Broadcast--|(3.8)               |            |     |
        |     |             |                    |            |     |
        |     |        (3.9)|-----Completed----->|            |     |
        |     |             |                    |            |     |
      ..|.....|.............|....................|............|.....|..
        |     |             |                    |            |     |

~~~
{: #phasethree-figure}


# The Commitment Sub-Protocol
{: #subprotocol}

Within Stage 3, the gateways must implement one (or more) transactional commitment sub-protocols
that permit the coordination between two gateways, and the final commitment of the asset transfer.

In the case that there are multiple commitment subprotocols supported by the gateways,
the choice of the sub-protocol (type/version) and
the corresponding commitment evidence must be negotiated between the gateways during Stage 1.

For example, in Stage 2 and Stage 3 discussed above
the gateways G1 and G2 may implement the classic 2-Phase or 3-Phase Commit (2PC or 3PC)
sub-protocol [Gray81] as a means to ensure efficient
and non-disputable commitments to the asset transfer.

Historically, transactional commitment protocols employ locking mechanisms
to prevent update conflicts on the data item in question.
When used within the context of digital asset transfers across networks,
the fact that an asset has been locked in NW1 must be communicated via an assertion to G2
(as the 3PC participant) in an indisputable manner.

Similarly, G2 must return a signed assertion to G1 that the asset has been regenerated (minted) in NW2.

These signed assertions must be verifiable by an authorized third party,
in the case that disputes occur (post event) or where legal audit
is required on the asset transfer.

The precise form of these assertions must be standardized
(for the given transactional commitment protocol) to eliminate any ambiguity.

# Security Considerations
{: #securityconsider}

As an asset network holds an increasing number of digital assets,
it may become attractive to attackers seeking to compromise the cryptographic keys of the entities,
services and its end-users.

Gateways are of particular interest to attackers
because they enable the transferal of digital assets to external networks,
which may or may not be regulated.
As such, hardening technologies and tamper-resistant crypto-processors
(e.g. TPM, SGX) should be used for implementations of gateways [HS2019].

# Policy Considerations
{: #policyconsider}

Digital asset transfers must be policy-driven
in the sense that it must observe and enforce
the policies defined for the network.
Resources that make-up a network are owned and operated by entities
(e.g. legal persons or organizations),
and these entities typically operate within regulatory jurisdictions [FATF].
It is the responsibility of these entities to translate
regulatory policies into functions on networks that
comply to the relevant regulatory policies.

At the application layer,
asset transfers must take into consideration
the legal status of assets and incorporate relevant asset-related policies
into their business logic.
These policies must permeate down to the gateways
that implement the functions of asset transaction processing.


# Compatibility Considerations
{: #compatibilityconsider}

As the asset transfer protocol must be completely agnostic
to the anatomy of a digital asset and to the type of ledger technology
underlying a system maintaining digital assets,
it must be compatible with different asset identification
standards like ISO 20022 and ITIN, and with standards for communicating
information about business processes (like ISO 20022).
Keeping the Stage-0 specification open and not tied to
a specific messaging or identification standard allows the
Secure Asset Transfer architecture to be flexible and inclusive,
and thereby meet compatibility goals.

--- back





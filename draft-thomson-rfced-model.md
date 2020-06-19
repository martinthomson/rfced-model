---
title: "A Proposed Model for RFC Editing and Publication"
abbrev: "RFC Editor Model"
docname: draft-thomson-rfced-model-latest
category: info

ipr: trust200902
area: IAB
workgroup: rfced-future
updates: 4844, 6635
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: M. Thomson
    name: Martin Thomson
    organization: Mozilla
    email: mt@lowentropy.net

normative:

informative:
   RPC-SA:
     title: "RFC Production Center Services Agreement"
     target: "https://iaoc.ietf.org/documents/ISOC-AMS-RPC-1Jan2016-Agreement-V1-Executed-PUBLIC.pdf"
     author:
       - ins: "IAOC"
     date: 2016-01-01


--- abstract

The finishing process for a document that is approved for publication as an RFC
currently involves a somewhat detailed and lengthy process.  The system that
executes that process involves a number of different actors, each bringing
competency with different aspects of the overall process.  Ensuring that this
process functions smoothly is critical to the mission of the organizations that
publish documents in the RFC series.

This document proposes a framework for that system that aims to provide clear
delineations of accountability and responsibility for each of the actors in this
system.


--- middle

# Introduction

The RFC Editor Model {{!MODEL=RFC6635}} describes a system that supports the
process of editing and publication of RFCs.

The process of RFC editing and publication takes inputs in the form of
documents that are approved for publication by one of four streams (IETF, IRTF,
IAB, and Idependent Submissions). The output is an RFC.

Generally speaking, this system is successful if RFCs are produced at a rate
approximating the rate that documents are approved for publication.  In addition
to managing throughput, the overall latency should be minimized and the quality
of documents should be sufficient to serve the ends of the consumers of those
documents.

In practice, the demands placed on the editing and publication process mean that
this function is quite involved. Furthermore, the exact goals that this system
serves continually evolves.  The current system has evolved out of a relatively
simple system, into something like what is described in {{!MODEL}} with multiple
discrete roles and somewhat complex interactions between each.

This document attempts to describe an evolution of the current model, drawing on
experience from successes and failures from operating that model, but based
purely on the very high-level abstraction of that system.

This document starts out by building from a simple (even simplistic) model of
the system, then builds that out incrementally.  The goal is to progressively
expand on the relevance of the model in addressing different problems that have
been identified as important, or to draw in each of the relevant actors in the
system and to attribute responsibilities (and associated authority) to each.


# Conventions and Definitions

{::boilerplate bcp14}


# Abstract Model

The highest-level abstraction is shown in {{model-base}}.

~~~
  +-------------+        +-------------+
  | IETF Stream +------->+             +----->
  +-------------+   D    |             |
  +-------------+   o    |             |
  | IRTF Stream +---c--->+ RFC         +-----> R
  +-------------+   u    | Editing     |       F
  +-------------+   m    | and         |       C
  | IAB Stream  +---e--->+ Publication +-----> s
  +-------------+   n    |             |
  +-------------+   t    |             |
  | Independent +---s--->+             +----->
  +-------------+        +-------------+
~~~
{: #model-base title="Simplified RFC Production Model"}

In this model, each of the four document streams produce documents that are
approved for publication according to the processes of those streams. Each
stream is an independent client of a single entity that provides services in
support of publishing documents as RFCs. These services have numerous facets,
but the core services are copy editing of documents, the preparation of
documents for publication, and the publication of documents.

At a high level, each of the streams is an independent customer of the function
of RFC Editing and Publication (REP).  Informally, the entity (or entities) that
perform the REP function are contracted to turn approved documents into RFCs.


# Funding and Oversight

The entity that performs the REP function holds contracts with the IETF LLC, who
also provides payment for those contracted services.  This means that the REP
function is ultimately answerable to the IETF LLC with respect to performance.

In practice, the IETF LLC delegates some of its authority to another body. This
allows the IETF LLC to rely on the expertise of volunteers from the community
in performing oversight. The IETF LLC currently delegates this function to the
RFC Series Oversight Committee (RSOC) via the IAB. This indirection has caused
some problems and this document proposes that oversight be a function that the
IETF LLC oversees directly.

The IETF LLC is therefore given direct authority over negotiating performance
targets for the REP and the responsibility of ensuring that those targets are
monitored. The IETF LLC is empowered to appoint a manager or to convene a
committee that is responsible for this oversight function.

Community members who have concerns about the performance of the REP can
request that the IETF LLC investigate the matter. If the IETF LLC opts to
delegate the oversight function, concerns can be raised with the IETF LLC. The
IETF LLC is ultimately responsible to the community via the mechanisms outlined
in its charter {{?LLC=RFC8711}}.

This results in evolving the basic model as shown in {{model-rsoc}}.

~~~
                              +------+
                              | IETF |
                              | LLC  |
                              +------+
                                 |
                                 | Contract &
                                 | Oversight
                                 v
+-------------+        +-------------+
| IETF Stream +------->+             +----->
+-------------+   D    |             |
+-------------+   o    |             |
| IRTF Stream +---c--->+ RFC         +-----> R
+-------------+   u    | Editing     |       F
+-------------+   m    | and         |       C
| IAB Stream  +---e--->+ Publication +-----> s
+-------------+   n    |             |
+-------------+   t    |             |
| Independent +---s--->+             +----->
+-------------+        +-------------+
~~~
{: #model-rsoc title="Oversight and Funding Functions"}

This shows the IETF LLC having budgetary and contractual oversight over the
REP.


## IETF LLC Delegation of Oversight Function

The current organization tasks the RSOC with responsibility for oversight. This
has lead to numerous questions about the extent of authority delegated to the
RSOC and the responsibilities of various entities that the RSOC is tasked with
interacting with.

This document avoids these questions by placing this authority directly with
the IETF LLC. However, the oversight function is one that the IETF LLC is
expected to delegate, either to an individual or committee.

Any delegation would ideally result in the creation of a a document governing
how the delegation was structured. This is not that document, but this assumes
that the person or persons who are given oversight responsibility would be
responsible for managing contract and performance for the RSEP. Any appeal or
dispute with the actions of this individual or committee would then be taken up
with the IETF LLC.


# Evolution and Setting Policies

Setting the policies that set targets for REP performance and more detailed
requirements for operation of their functions has historically been delegated to
the RSOC.  This document proposes separating that function.  The goal is to
improve the ability of the community (across all streams) to set and evolve
policies.

The requirements of each of the streams changes over time.  The goal is to find
a system that allows the community to develop consensus around the strategic
direction for the evolution of the RFC Series.

In terms of structure of this effort, the community has a set of well-understood
and tested systems for developing consensus.  Therefore, this document proposes
that strategic goals for the RFC Series are developed using the working group
process {{!WG=RFC2418}} used in the IETF.

Concretely, this proposes forming a RFC Series Evolution program of the IAB that
uses the auspices of an IAB program, one that closely follows the model proposed
in {{?RSEME=I-D.flanagan-rseme}}.  This results in a group that follows
{{!WG=RFC2418}} procedures, with the exception that the functions performed by
the IESG are instead performed by the IAB.  In particular, selection of chairs
and appeals regarding the execution of the process are directed to the IAB to
resolve.

It is important that this group adopt code of conduct, anti-harrassment, and
other policies.  Again, existing IETF processes - collectively referred to in
the Note Well - are well-suited to this task.

Any strategic direction that is produced by this process will be documented in
RFCs. These will need to be framed as high-level goals and priorities rather
than strict requirements. It will be up to the IETF LLC - or their delegate -
to negotiate with the REP function about the execution for any changes. In
negotiating the execution of strategy, the IETF LLC is expected to factor in
relevant factors such as cost, legal constraints, or schedule.

The IETF LLC is also responsible for ensuring that the plans for implementation
of strategic goals is published and available to the community.

This results in the model shown in {{model-rse}}.

~~~
                              +------+
                              | IAB  |
                              +--+---+
                                 |
                                 | Oversight
                                 v
                           +-----+------+
                           | RFC Series |
                           | Evolution  |
                           | Program    |
                           +-----+------+
                                 |
                                 | Strategy
                                 v
                              +--+---+
                              | IETF |
                              | LLC  |
                              +--+---+
                                 |
                                 | Contract &
                                 | Oversight
                                 v
+-------------+        +---------+---+
| IETF Stream +------->+             +----->
+-------------+   D    |             |
+-------------+   o    |             |
| IRTF Stream +---c--->+ RFC         +-----> R
+-------------+   u    | Editing     |       F
+-------------+   m    | and         |       C
| IAB Stream  +---e--->+ Publication +-----> s
+-------------+   n    |             |
+-------------+   t    |             |
| Independent +---s--->+             +----->
+-------------+        +-------------+
~~~
{: #model-rse title="Evolution and Strategy Additions"}


## Individual Interactions

It is important to recognize that the interface to the REP function is most
often through individual authors (or chairs, document shepherds, and area
directors) and individual REP staff.

In those interactions, those individuals might find problems with processes or
might be inclined to make suggestions for improvement.  The goal of the RFC
Series Evolution program is to provide a single venue for discussion of changes
to REP requirements, processes, and procedures.


## The Needs of Different Streams

The singular group responsible for evolution of the RFC Series as a whole is
a simplification that is made to reduce contention in setting strategic goals.
It is important to note that the needs of different streams can be different.

Several factors motivate a single group that sets strategy.  Historically, the
IETF stream is responsible for a large proportion of the documents in the
series.  That is unlikely to change and experience has shown that other streams
are - for the most part - willing to accept that strategic direction is largely
dictated by the needs of the most prolific user of the REP service.

It is important that each stream retain control over the content of documents
that are published on that stream.  Streams currently appoint a stream manager
who is allocated authority over content on that stream and responsibility to
manage any problems that might arise in handling documents produced by that
stream.  This document proposes that this aspect of the role continue.

Stream managers are also involved in discussion of changes to REP processes.
Rather than deal with issues of REP processes directly, stream managers are
expected to initiate discussion or make proposals to the RFC Series Evolution
program. To avoid conflicts of interest, it is expected that stream managers
will be active participants - and not chairs - in this program.


# Tooling

Producing an RFC relies heavily on tools that help automate many aspects of the
process.  Using tools contributes to consistency and better performance of the
REP function.

In one version of this model, the tools that are used by the REP function are
the responsibility of the function.  However, the larger system benefits from a
degree of consistency between the tools used by each stream to produce documents
and the tools used in the editing and publication stage.  In practice, these
tools are shared and a great deal of benefit is derived from that arrangement.

A number of different organizational arrangements could be conceived of for
arranging this situation. For instance, the REP could be tasked with producing
and maintaining tools that it is required to also make available to the
community of people that produce documents. The current arrangement is that the
REP develops some of its own tools, but it also depends on tools that are
maintained by the IETF LLC.

Reflecting that arrangement, we have the final composition of functions as
shown in {{model-final}}.

~~~
                                +------+
                                | IAB  |
                                +--+---+
                                   |
                                   | Oversight
                                   v
                             +-----+------+
+-------------+ Participate  | RFC Series |
|  Community  +------------->+ Evolution  |
+-----+-------+              | Program    |
      ^                      +-----+------+
      |                            |
      | Provide Tools              | Strategy
      |                            v
+-----+-------+                 +--+---+
|    Tools    |     Contract(s) | IETF |
| Maintenance +<----------------+ LLC  |
+-----+-------+                 +--+---+
      |                            |
      +--Provide-Tools-------+     | Contract &
                             |     | Oversight
                             v     v
  +-------------+        +---+-----+---+
  | IETF Stream +------->+             +----->
  +-------------+   D    |             |
  +-------------+   o    |             |
  | IRTF Stream +---c--->+ RFC         +-----> R
  +-------------+   u    | Editing     |       F
  +-------------+   m    | and         |       C
  | IAB Stream  +---e--->+ Publication +-----> s
  +-------------+   n    |             |
  +-------------+   t    |             |
  | Independent +---s--->+             +----->
  +-------------+        +-------------+
~~~
{: #model-final title="Final Model"}

This arrangement means that any dependencies the REP might have for tools need
to be coordinated via the entity responsible for managing the maintenance of
tooling. The IETF LLC is ultimately responsible for ensuring that the tools
maintenance function has processes for managing the requirements of the REP.

If meeting new requirements from the RSOC require new or modified tooling, it
is the responsibility of the REP to formulate requests regarding to tools to
the Tools Maintenance function.

Any problems arising from this arrangement will be raised with the RSOC as they
pertain to meeting operational goals.


# Management of Individual Functions

This model does not specify strong requirements on the management of any of the
functions it describes. It is expected that each function identified here will
be managed in a manner appropriate to the function that it serves.

Any choice by the IETF LLC to delegate oversight responsibility to a committee
might require that the committee will need decision-making processes. The IETF
LLC is ultimately responsible for ensuring that these processes are appropriate
and effective.

The choice of leadership for the RFC Series Evolution program could become more
important with a move to a system that lacks a single figurehead. Two measures
are suggested to mitigate the potential for this position to become a function
replacement for the RSE position:

* The IAB should appoint at least two co-chairs. This is already good practice
for working groups as it provides redundancy in case of absence or conflict of
interest.

* The IAB should seek new chairs at regular intervals and seek to limit the
period over which any one individual might hold a leadership position in the
program.

These are suggestions to the IAB only, not hard requirements.

If the function of the REP is contracted to a single entity, it would be the
responsibility of that entity to provide appropriate management. That
management would be expected to manage the workload involved in providing core
REP functions like editing and publication, arranging and planning for changes
in response to upcoming requirements, and reporting on status and performance.

For the tools maintenance function, contracting of tools development and
maintenance currently involves multiple entities. Therefore, it might be
necessary for the IETF LLC to contract for a role to manage coordination of
tools maintenance. Arranging for appropriate management, along with systems for
establishing accountability to the community, enabling community contributions,
and dealing with dispute or contention is left to the IETF LLC.


# Other Involved Entities

Many documents involve actions for IANA that are processed as part of the REP
processing. These processes need to be captured and documented.

This draft describes a model whereby the RFC Series Advisory Group and the RFC
Series Editorial Board have no future as these are functions that serve the a
role that does not exist in this model.  These august bodies embody a great deal
of collected wisdom regarding the RFC Series.  It is this author's earnest hope
that these individuals will continue to lend their efforts in the form of
contributions to the development of strategy.

This draft proposes that the RFC Series Oversight Committee (RSOC) be
disbanded. Many of the functions provided by the RSOC are now an IETF LLC
responsibility in this model. If the IETF LLC decides to form a committee, the
experience of RSOC procedures and former personnel might be used as a resource.


# Notable Differences from Version 2

This proposal does not describe a role for a RFC Series Editor.

The functions previous served by this individual are devolved into several
pieces. The REP function is expanded to cover both RFC Production Center (RPC)
and RFC Publisher as well as the operational management responsibilities
formerly adopted by the RFC Series Editor.

The responsibility for managing the evolution of the series is delegated to a
consensus-based group rather than being vested in an individual. Previous RFC
Series Editors achieved much of the strategic and evolutionary functions of
their role by building community consensus, so this aspect of the role is
essentially transferred to the chairs of the RFC Series Evolution program.

Any responsibility for execution of RFC Series strategy that might have been
the responsibility of a RFC Series Editor has been distributed: the IETF LLC is
responsible for turning strategy into requests; the REP is responsible for
executing these requests. As the RPC (or publisher) was previously ultimately
responsible for execution of any strategy, the functional difference is
minimal.

Moving away from a model where a single individual is involved in setting
direction for the RFC Series is significant.  This proposal vests that control
in a consensus-based body instead, which means that decisive action is likely no
longer a feature of this system.  As the emphasis of the group is on longer-term
strategy, this is not anticipated to be a practical problem.

This proposal combines the RFC Production Center and RFC Publisher functions.
These have been conjoined in practice for many years already and so this merely
formalizes a standing arrangement.


# Documentation Requirements

This model depends on the production of a document (or set of documents) that
outlines the initial set of requirements for the operation of the REP. Much of
this already exists in the form of previous service agreements {{RPC-SA}} and
the expectation is that these documents can be adapted. These documents will
become the resposibility of the IETF LLC.

Over time, some of the material from service agreements and contract are
expected to move to strategic documents maintained by the RFC Series Evolution
program.

The RFC Series Evolution program will be responsible for maintaining this
document, along with other documents that describe the RFC Series, such as
{{?MODEL}}, {{?RFC-SERIES=RFC6635}}, and {{?BOILERPLATE=RFC7841}}. Continuing
publication of these documents on the IAB represents no change to existing
practice.


# Errors and Omissions

This is a draft. At this stage, it is intended to just show the general outline
of the model. As details are filled in, everything here is liable to change.
There are likely many errors, omissions, and inconsistencies.

There are lots of small details in {{!MODEL}} that are still
likely relevant and would need to be tweaked to fit within the proposed
structure.


# Security Considerations

Much of the success of systems like this can be attributed to the dilligent work
of individuals who strive to resolve issues collaboratively.  Generally
speaking, it is good to assume that this will continue.  However, this document
does attempt to establish where authority lies for any particular decision in
case of lapses or disagreements.

This document aims to provide some measure of security against failure of any
single person to execute their function in good faith.  That doesn't mean that a
malicious actor operating in any of the critical roles could not choose to be
extremely disruptive.  In addition to some expectation of reasonableness, this
system defines entities (often bodies) to whom each actor is answerable or who
are empowered to resolve disputes.


# IANA Considerations

This document makes no request of IANA.


--- back

# Acknowledgments
{:numbered="false"}

This is not new thinking.  You might, if you were so inclined, find all of these
concepts in emails or documents from other people.

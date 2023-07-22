---
v: 3

title: "COSE: On Registration Principles"
abbrev: "COSE Registration Principles"
docname: draft-bormann-cose-registration-principles-latest

category: info
submissiontype: IETF  # also: "independent", "IAB", or "IRTF"
date:
consensus: true
area: "Security"
workgroup: "CBOR Object Signing and Encryption"
keyword:

venue:
  group: "CBOR Object Signing and Encryption"
  mail: "cose@ietf.org"
  github: "cabo/cose-regprin"

author:
  -
    ins: C. Bormann
    name: Carsten Bormann
    org: Universität Bremen TZI
    street: Postfach 330440
    city: Bremen
    code: D-28359
    country: Germany
    phone: +49-421-218-63921
    email: cabo@tzi.org


informative:
  STD96:
    -: cose
  STD94:
    -: cbor
    =: RFC8949
  IANA.cose:
#  RFC8610: cddl
  RFC8126:
  RFC8152:
  RFC9053:


--- abstract

[^abs1-]

[^abs1-]:
    COSE (STD 96, RFC 9052 and RFC 9338) defines a number of
    registries that allow registrants to exercise the numerous
    extension points defined in COSE.
    Section 11.6 of RFC 9052 gives the Designated Experts for these
    registries considerable leeway in deciding about registration
    requests.

[^abs2-]

[^abs2-]:
    The present document is intended to collect information that has
    been the basis for initial population of and further registration
    in these registries.
    It is intended to be shaped by the Designated Experts and serve
    them as a collective memorandum and a checklist.
    As a secondary function, it is also intended to help registrants
    create registrations that are acceptable to the Designated
    Experts.

[^abs3]

[^abs3]:
    Revision -00 of this draft is an early skeleton that should allow us
    to decide whether such a collection of information is useful and
    whether we want to flesh out this document.

--- middle

# Introduction

[^abs1-]

Specifically, {{Section 11.6 of RFC9052}} says:

{:quote}
> 11.6.  Expert Review Instructions
>
> All of the IANA registries established by [RFC8152] are, at least in
> part, defined as Expert Review [RFC8126].  This section gives some
> general guidelines for what the experts should be looking for, but
> they are being designated as experts for a reason, so they should be
> given substantial latitude.

({{RFC8152}} is the previous edition of what is now {{RFC9052}} and
{{RFC9053}}; this document established the registries being discussed,
which together make up the {{IANA.cose}} registry group.)

The further text of {{Section 11.6 of RFC9052}} gives instructions about
the general operations of the registries, but does not discuss the
architectural and structural principles that might go into a
registration decision.

[^abs2-]

[^abs3]

## Conventions and Definitions

The definitions of {{STD94}} and {{STD96}} apply.

# COSE Registration Principles

[^warning]

[^warning]: This section is a skeleton and needs to be fleshed out.

At the time of writing, some 172 registrations have been made in the
COSE registry group {{IANA.cose}}.
These can serve as a body of examples how to make registrations.
Unfortunately, not all registrations in this set demonstrate
outstanding consistency in decision making, so this section will
collect information about where existing registration decisions turned
out to be suboptimal or at least different in structure than
registrations of a similar nature.

## General Considerations

Code Point Frugality:

: COSE is designed to work in environments where at least some of the
devices have limited resources; curation of codepoints so that the
ones that are most frequently used with such constrained devices
receive the codepoints with the shortest representation (and can
continue to do so over a number of decades) is always an objective.

## COSE Header Parameters

...

## COSE Header Algorithm Parameters

...

## COSE Algorithms

Algorithm identifiers in these registrations have a *Recommended* Tag,
which indicates ({{Section 16.4 of RFC8152}}):

{:quote}
>   Recommended:
>   : Does the IETF have a consensus recommendation to use
      the algorithm?  The legal values are 'Yes', 'No', and
      'Deprecated'.

Note that an algorithm can be *deprecated* already at registration time.
This value was used in the registration of the
{{?I-D.ietf-cose-aes-ctr-and-cbc}} values which only can be used under
very specific conditions.

Algorithm identifiers are usually assigned so that a single identifier
stands for a collection of underlying algorithms, with main parameters
such as key or hash length chosen, so that a single algorithm
identifier suffices to fully characterize the cryptographic operations.
A key is the obvious exception, but also parameters that go with a key
such as its curve type.

Where a certain underlying algorithm has a small number of possible
parameter sets, all registrations for the use of that underlying
algorithm in a COSE Algorithm are made at the same time.  For
instance: A128GCM (AES-GCM mode w/ 128-bit key, 128-bit tag) we
registered together with A192GCM (AES-GCM mode w/ 192-bit key, 128-bit
tag) and A256GCM (AES-GCM mode w/ 256-bit key, 128-bit tag).
The expert (in this case the author of {{RFC9053}}) did not make
separate assessments how useful or desirable the individual parameter
sets were going to be, but registered them all at once.
When the collection of
AES-CCM-16-64-128, AES-CCM-16-64-256,
AES-CCM-64-64-128, and AES-CCM-64-64-256, as well as
AES-CCM-16-128-128, AES-CCM-16-128-256,
AES-CCM-64-128-128, and AES-CCM-64-128-256 were registered, these were
also registered all at once, but grouped into two groups with
different representation sizes of the algorithm identifier.

## COSE Key Common Parameters

...

## COSE Key Type Parameters

...

## COSE Key Types

...

## COSE Elliptic Curves

...

# Security Considerations

This document is about registrations in registries that have direct
security impact; security considerations that require discussion
beyond that are mentioned in the discussions above.

# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

This document was motivated by a discussion at IETF 117 Hackathon.
The author is grateful to the many contributors to the discussions on
the mailing lists that build the basis for this document.

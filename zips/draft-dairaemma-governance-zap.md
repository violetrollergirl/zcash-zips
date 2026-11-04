
    ZIP: Unassigned
    Title: Zcash Adoption Pool (ZAP)
    Owners: Daira-Emma Hopwood <daira@jacaranda.org>
    Credits: Violet Rollergirl
             Blake Benthall (emersonian)
             Mylo Bennett
             Alison Stevenson
    Status: Draft
    Category: Consensus Process
    Created: 2026-10-30
    License: MIT
    Discussions-To: <https://forum.zcashcommunity.com/t/zcash-adoption-pool-zap/58656>
    Pull-Request: <https://github.com/zcash/zips/pull/1431>


# Terminology

The key words "MUST", "SHALL", "SHOULD", "SHOULD NOT", and "MAY" in this
document are to be interpreted as described in BCP 14 [^BCP14] when, and
only when, they appear in all capitals.

The terms "Mainnet" and "Testnet" are to be interpreted as defined in the
Zcash protocol specification [^protocol-networks].

The terms "Zcash Community Grants" (or "ZCG"), "ZCG Committee", and
"Deferred Dev Fund Lockbox" are to be interpreted as defined in ZIP 1015
[^zip-1015]; "Protocol-defined Ecosystem Funding" and "Coinholder-Controlled
Fund" as defined in ZIP 1016 [^zip-1016].

"ZEC" refers to the native currency of Zcash on Mainnet.

"Adoption" means an increase in the number of natural persons who hold ZEC
directly or transact directly in ZEC on the Zcash network.

A "stakeholder" is a party whose routine economic activity depends on the
continued operation of the Zcash network.

A "disbursement chain" is the sequence of ZEC transfers from a ZAP grant to
its "grant recipient", through zero or more "intermediary recipients", to
one or more "end recipients" (natural persons).

A "computational attack" targets consensus; its cost is denominated in
hashrate, hardware, or energy. A "political attack" targets the network's
ability to be used; its cost is denominated in legislative, regulatory,
legal, reputational, or market-access capital. Examples of the latter:
delisting, deplatforming of developers or infrastructure, hostile
legislation, enforcement action against intermediaries, reputational
campaigns.


# Abstract

The portion of Protocol-defined Ecosystem Funding allocated to ZCG is
reaffirmed and bound to its stated objective in ZIP 1015 [^zip-1015-zcg]:
increasing Zcash adoption as broadly as possible. The pool is renamed the
"Zcash Adoption Pool" and a minimum assessment criterion is specified for
grants disbursed from it.

Adoption is hashrate against political attack.


# Motivation

## Mandate

ZIP 1015 specifies:

> The stream allocated to Zcash Community Grants (ZCG) is intended to fund
> independent teams entering the Zcash ecosystem, to perform major ongoing
> development (or other work) for the public good of the Zcash ecosystem, to the
> extent that such teams are available and effective. The ZCG Committee is given
> the discretion to allocate funds not only to major grants, but also to a
> diverse range of projects that advance the usability, security, privacy, and
> adoption of Zcash, including community programs, dedicated resources, and other
> projects of varying sizes.

Capital requirements of projects satisfying these criteria exceed
available funding.

## Threat model

A privacy-preserving payment network faces computational and political
attacks. The historical record of privacy technologies shows political
attacks to be the more frequent and the more effective. Of the Zcash block
subsidy, 80% is allocated against computational attack via the miner
reward; the `FS_FPF_ZCG_H3` stream, 8%, is the only allocation that can be
directed against political attack. This ZIP does not resize the stream; it
records the gap and designates the stream's purpose so that later proposals
can address it.

The political adversary is plural and need not be hostile in intent.
Regulators act to retain control over settlement, payment incumbents to
preserve margin, competing networks to acquire share, legislators on the
preferences of the most visible constituency. Each will act against the
network whenever doing so is cheap relative to the benefit. The network's
objective is therefore not persuasion but alteration of the adversary's
cost function.

## Cost model

An adversary is deterred when the cost of its aim exceeds the benefit. For
a political attack, the cost is that of removing enough stakeholder
dependencies that the network can no longer be used for the adversary's
purpose; it depends on how many dependencies must be removed and on what
each costs to remove.

The number is small when stakeholders are concentrated in one exchange,
jurisdiction, developer organization, or sector: a single point at which
effort can be applied at bounded cost. It grows with the count of
jurisdictions, sectors, and political alignments across which stakeholders
are distributed, because no single removal then suffices.

The cost per dependency is highest for stakeholders for whom shielded
settlement is an operational requirement rather than a preference, and who
are outside the adversary's reach; such stakeholders contest their own
removal with their own resources. It is near zero for parties with no
economic dependency on the network, whatever their stated preferences.
Adoption converts the second kind of party into the first, most cheaply
before the adversary has chosen its time and lever.

## Assessment

A grant whose proceeds stop at the grant recipient adds at most one
stakeholder; proceeds transferred onward in ZEC add one at each hop:

    ZAP -> grant recipient -> [intermediary recipient(s)] -> end recipient(s)

A grant's expected contribution is therefore proportional to the expected
number of distinct parties in its disbursement chain. Assessment SHOULD
weight the expected fan-out of the chain and the proportion of recipients
for whom shielded ZEC is an operational requirement, on the evidence in the
application.

The metric is distinct shielded receives, not transaction count. Outflows
(for example ZEC-to-BTC swaps) inflate transaction count while terminating
the chain and removing a stakeholder. Assessment SHOULD therefore rank
receipt metrics (external-asset-to-shielded-ZEC, and preferably
shielded-ZEC-to-shielded-ZEC) above spend metrics, balance held, or
undifferentiated transaction count.

Measurement costs adoption. This criterion SHOULD NOT be read to require
evidence that is not realistically obtainable or whose collection would
reduce adoption or compromise recipient privacy. Collection of information
on intermediary or end recipients MUST be limited to what is necessary to
assess grant effectiveness, MUST be aggregated or otherwise anonymized (for
example by retaining only summary statistics), and MUST be performed only
with the informed consent of the parties concerned.

## Background

Proposals have periodically been made to withdraw funding from independent
teams entering the Zcash ecosystem. The most recent rest on a reading of
"development" restricted to protocol engineering, which is inconsistent
with the text of ZIP 1015 quoted above and with its documented intent,
which ZIP 1016 did not alter.

Under the model above, concentrating allocation authority in any single
class of participant narrows the dependency graph and reduces the number of
dependencies an adversary must remove; this holds for large holders and for
the grant committee alike. Breadth of allocation is a security property,
not a distributional preference. ZEC holders are also the principal
beneficiaries of adoption: velocity and breadth of distribution are the
inputs to liquidity, and liquidity is what holders are exposed to.
Proposals that treat holder and adoption interests as opposed are evaluated
against the model, not against their proposers.

A separate argument holds that development can be funded by private
capital and therefore should be. Capital with an external principal carries
an external exit condition; the funding stream has none. This ZIP addresses
the programmes private capital has not funded. The two sources are
complementary.


# Requirements

All requirements of ZIP 1015 continue to apply; in particular:

* There is a well-defined, publicly agreed process for evaluation of, and
  community feedback on, grant proposals.
* Any use of Deferred Dev Fund Lockbox funds is consistent with the purpose
  specified in [^zip-1015-lockbox] of "funding grants to ecosystem
  participants".

In addition, funds disbursed through the Zcash Adoption Pool are to be
further disbursed for the explicit purpose of adoption as defined above.


# Non-requirements

* Unanimity among stakeholders.
* Per-recipient auditability beyond aggregate statistics.
* Any change to the amount or duration of the `FS_FPF_ZCG_H3` stream.
* Enumeration of recipient categories. The criterion is defined by
  mechanism, not by identity of recipient.


# Specification

For avoidance of doubt, the `FS_FPF_ZCG_H3` funding stream SHALL continue
at its existing value and for the duration specified in ZIP 214 Revision 3
[^zip-0214], on Mainnet and Testnet.

The pool of funds associated with this stream SHALL be renamed "Zcash
Adoption Pool" ("ZAP"), the grant programme by which it is disbursed "Zcash
Adoption Pool Grants" ("ZAP Grants"), and the ZCG Committee the "ZAP
Committee". Assets associated with ZCG (past, present, or future) become
assets of the Zcash Adoption Pool; requirements on their administration in
ZIPs 1015 and 1016 [^zip-1015] [^zip-1016] are unchanged.

The ZAP Grant assessment process MUST establish reasonable confidence, on
the evidence in the application, that funds disbursed will be further
disbursed for the explicit purpose of adoption as defined above.

The ZAP Committee MAY publish non-normative assessment guidance, including
on recipient categories expected to contribute most to adoption. Such
guidance is not part of this ZIP.


# Acknowledgements

The authors thank the attendees of the Zcon7 conference for the discussions
leading to this proposal, and the organizers for the venue.


# References

[^BCP14]: [Information on BCP 14 — "RFC 2119: Key words for use in RFCs to Indicate Requirement Levels" and "RFC 8174: Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words"](https://www.rfc-editor.org/info/bcp14)

[^protocol-networks]: [Zcash Protocol Specification, Version 2026.8.0 [NU6.3]. Section 3.12: Mainnet and Testnet](protocol/protocol.pdf#networks)

[^zip-0214]: [ZIP 214: Consensus rules for a Zcash Development Fund](zip-0214.rst)

[^zip-1015]: [ZIP 1015: Block Subsidy Allocation for Non-Direct Development Funding](zip-1015.rst)

[^zip-1015-zcg]: [ZIP 1015: Block Subsidy Allocation for Non-Direct Development Funding — Zcash Community Grants](zip-1015#zcash-community-grants-zcg)

[^zip-1015-lockbox]: [ZIP 1015: Block Subsidy Allocation for Non-Direct Development Funding — Lockbox](zip-1015#lockbox)

[^zip-1016]: [ZIP 1016: Community and Coinholder Funding Model](zip-1016.md)

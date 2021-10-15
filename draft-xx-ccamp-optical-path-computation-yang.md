---
coding: utf-8

title: YANG Data Models for requesting Path Computation in Optical Networks

abbrev: Yang for Optical Path Computation
docname: draft-xx-ccamp-optical-path-computation-yang-00
workgroup: CCAMP Working Group
category: std
ipr: trust200902

stand_alone: yes
pi: [toc, sortrefs, symrefs, comments]

author:
  -
    name: Italo Busi
    org: Huawei Technologies
    email: italo.busi@huawei.com
  -
    name: Aihua Guo
    org: Futurewei Technologies
    email: aihuaguo.ietf@gmail.com
  -
    name: Sergio Belotti
    org: Nokia
    email: sergio.belotti@nokia.com

contributor:
  -
    name: Daniel King
    org: Old Dog Consulting
    email: daniel@olddog.co.uk

--- abstract

This document describes YANG data models for Remote Procedure Calls (RPCs) to request Path Computation in Optical Networks (OTN, WSON and Flexi-grid).

The YANG data models defined in this
document conforms to the Network Management Datastore Architecture
(NMDA).

--- middle

# Introduction

{{!I-D.ietf-teas-yang-path-computation}} describes some use cases, where a client needs to request
underlying SDN controllers for path computation. In some of these use cases the underlying SDN controller can control a single-layer (OTN, WSON or Flexi-grid) or multi-layer Optical network.

This document define YANG data models, which augment the generic Path Computation RPC defined in {{!I-D.ietf-teas-yang-path-computation}}, with technology-specific augmentations required to request path computation to an Optical underlying SDN controller.

The YANG data model defined in this document conforms to the Network
Management Datastore Architecture {{!RFC8342}}.

## Terminology and Notations 

  Refer to {{!RFC7446}} and {{!RFC7581}} for the key terms used in this
  document.  The following terms are defined in {{!RFC7950}} and are not
  redefined here:

  *  client

  *  server

  *  augment

  *  data model

  *  data node

  The following terms are defined in {{!RFC6241}} and are not redefined
  here:

  *  configuration data

  *  state data

  The terminology for describing YANG data models is found in
  {{!RFC7950}}.

## Tree Diagram

  A simplified graphical representation of the data model is used in
  {{optical-pc-tree}} of this document.  The meaning of the symbols in these
  diagrams is defined in {{!RFC8340}}.

## Prefix in Data Node Names

  In this document, names of data nodes and other data model objects
  are prefixed using the standard prefix associated with the
  corresponding YANG imported modules, as shown in the following table.

| Prefix       | YANG module                      | Reference
| l0-types     | ietf-layer0-types                | {{!RFC9093}}
| l0-types-ext | ietf-layer0-types-ext            | {{!I-D.ietf-ccamp-layer0-types-ext}}
| l0-types     | ietf-layer0-types                | {{!RFC8776}}
| l1-types     | ietf-layer1-types                | {{!I-D.ietf-ccamp-layer1-types}}
| te           | ietf-te                          | {{!I-D.ietf-teas-yang-te}}
| tep          | ietf-te-path-computation         | {{!I-D.ietf-teas-yang-path-computation}}
| flexg-pc     | ietf-flexi-grid-path-computation | This Document         
| wson-pc      | ietf-wson-path-computation       | This Document         
| otn-pc       | ietf-otn-path-computation        | This Document         
{: #tab-prefixes title="Prefixes and corresponding YANG modules"}

# YANG Data Models for Optical Path Computation 

## YANG Models Overview

The YANG data models for requesting WSON, Flexi-grid and OTN path computation are defined as augmentations of the generic Path Computation RPC defined in {{!I-D.ietf-teas-yang-path-computation}}.

TBA: a figure showing the module relationship

The entities and TE attributes, such as requested path and tunnel attributes, defined in {{!I-D.ietf-teas-yang-path-computation}}, are still applicable when requestiong WSON, Flexi-grid and OTN path computation and the models defined in this document only specifies the additional technology-specific attributes/information, using the attributes defined in {{!RFC9093}}, {{!I-D.ietf-ccamp-layer0-types-ext}} and {{!I-D.ietf-ccamp-layer1-types}}.

The YANG modules ietf-wson-path-computation, ietf-flexi-grid-path-computation and ietf-otn-path-computation defined in this document conforms
to the Network Management Datastore Architecture (NMDA) defined in
{{!RFC8342}}.

## Attributes Augmentation

The common characteristics for layer 0 (WSON and Flexi-grid) tunnels are under definition in {{!I-D.ietf-ccamp-layer0-types-ext}} and re-used in the ietf-wson-path-computation and ietf-flexi-grid-path-computation YANG models

{: #optical-te-bandwidh}

## Bandwidth Augmentation

As described in Section 4.2 of {{!RFC7699}}, there is some overlap
between bandwidth and label in layer0.

The WSON and flexi-grid label resource information described in {{optical-te-label}},
is sufficient to describe also the spectrum resources within WSON and
flexi-grid networks. Therefore, the model does not define any augmentation
for the te-bandwidth containers defined in {{!I-D.ietf-teas-yang-path-computation}}.

The OTN path computation model augments all the occurrences of the te-bandwidth container
with the OTN technology specific attributes using the otn-link-bandwidth and otn-path-bandwidth groupings defined in {{!I-D.ietf-ccamp-layer1-types}}.

{: #optical-te-label}

## Label Augmentations

The models augment all the occurrences of the label-restriction list
with WSON, Flexi-grid and OTN technology specific attributes using the 
l0-label-range-info and flexi-grid-label-range-info groupings defined in {{!RFC9093}} and the
otn-label-range-info grouping defined in {{!I-D.ietf-ccamp-layer1-types}}.

Moreover, the models augment all the occurrences of the te-label
container with the WSON, Flexi-grid and OTN technology specific attributes using the
wson-label-start-end, wson-label-hop, wson-label-step,
flexi-grid-label-start-end, flexi-grid-label-hop and flexi-grid-label-step defined in {{!RFC9093}} and the
otn-label-start-end, otn-label-hop and otn-label-step groupings defined in {{!I-D.ietf-ccamp-layer1-types}}.

{: #optical-pc-tree}

# Optical Path Computation Tree Diagrams

{: #wson-pc-tree}

## WSON Path Computation Tree Diagrams

{: #flexg-pc-tree}

## Flexi-grid Path Computation Tree Diagrams

{: #otn-pc-tree}

## OTN Path Computation Tree Diagrams

{: #optical-pc-yang}

# YANG Models for Optical Path Computation

{: #wson-pc-yang}

## YANG Model for WSON Path Computation

{: #flexg-pc-yang}

## YANG Model for Flexi-grid Path Computation

{: #otn-pc-yang}

## YANG Model for OTN Path Computation

# Manageability Considerations

  TBD. 

# Security Considerations

  \<Add any security considerations>

# IANA Considerations

  \<Add any IANA considerations>

--- back

{: numbered="false"}

# Acknowledgments

   This document was prepared using kramdown.
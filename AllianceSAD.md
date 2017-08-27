Dun & Bradstreet has formed a strategic alliance with Microsoft, whereby D&B
will deliver pre-mastered business data throughout the Microsoft Ecosystem via the Common Data Service (CDS).
The purpose of this document, is to present a cohesive story that represents the desires of product and the needs of technology.

In addition to the near and mid-term requirements, this document will also capture the needs for a demonstration that will take place on September 25th at Microsofts annual, world-wide conference(s), Ignite & Envision.

# Conceptual Overview
The partnership has identified a high-level solution that comprises of firmographic data being accessible to Microsofts enterprise customers (required to be a D&B customer) from within the Common Data Service. The CDS is an emerging cloud store that promises to offer consistency across a myriad of products and technologies within Microsofts larger enterprise ecosystem.

As an enterprise customer of Microsoft (defined by the level of license agreement), each customers tenanted environment will be pre-populated with the CDS and the baseline entities it comprises.

D&B data will be provided to customers in a targeted form, based on a subset of the CMPELK data currently referred to as the Kernel. The kernel provides immediate value that will support a variety of business functions while establishing the baseline for incorporating additional, more targeted packages such as those aligned to various lines of business (i.e. Risk, Credit, Sales & Marketing etc).

The CDS is quickly evolving in to the preferred, centralized data store for all platforms within the ecosystem. Such platforms within the ecosystem that will receive direct benefit today include;

* PowerApps
* LogicApps
* FunctionApps
* Power BI
* Flow

Indirectly, Dynamics CRM and Dynamics ERP can interoperate with the CDS through an interim solution known as the Data Integrator. Microsofts aggressive roadmap currently has the Dynamics & CDS teams converging around February 2018, whereby Dynamics will sit directly over the CDS, serving as its primary persistence layer. Around that same time, the Dynamics team plan to release its XRM platform to market, a solution that is positioned to rival the likes of force.com, enabling customers, 3rd party and 1st party providers to release enterprise class applications without the need for Sales or ERP.

-----------------

DIAGRAM - Ecosystem Overview

-----------------

The CDS will be the primary catalyst for initiating the request for data within its store to be cleaned, matched and appended. This will be performed in concert with Microsofts workflow engine, Flow. Flow will orchestrate the D&B actions to match and append through workflow definitions known as flows.
Flows are activated via a trigger. The primary triggers for the D&B related flows will be from the account entity within the CDS. Each time an account is created or updated, an associated flow (designed, released and managed by D&B) will determine if it needs to perform a match and/or an append.

If deemed necessary, the actions (i.e. match, append) will connect to the Direct+ APIs through a pre-configured connection (environment instance of a connector). The actions on the connection are responsible for making the calls to Direct+, marshaling the response and any additional exception handling.

-----------------




DIAGRAM - Flow Overview




-----------------

Once the account has been decorated with firmographic data, the platforms listed above will have immediate access to perform any number of value-added capabilities ranging from;
* Reporting
* Analytics
* Business based functions (i.e. field automation, segmentation etc.)
* Workflows
* Logic based functions (i.e. lead scoring, routing, alignment etc.)

The goal of the alliance is to provide customers and partners the ability take immediate advantage of D&Bs data throughout the Microsoft ecosystem, realizing benefits not previously afforded to them. Furthermore, it establishes a baseline that allows them to take advantage of D&Bs broader set of business data and those of its partner network.

## THE OFFERING


## GO-TO-MARKET


# Solution
While the ecosystem covers a lot of ground and the realized benefit of this solution is even greater, this section will cover the key aspects of the solution.

## KERNEL
The Kernel is the branded packet of data that represents the entry-level dataset. It is a subset of the CMPELK product from Direct+ and has been curated by folks from both Microsoft and D&B to ensure the minimum set provides the appropriate level of value.

### Attributes

Following are the attributes that have been identified for the Kernel. Note these will be mapped from the Kernel directly to the BusinessProfile entity; an entity that relates to a variety account types within the CDS (i.e. Organization, Partner, Supplier etc.).

attr1
.
.
.
.
.
.
attrn

### Entity Mapping
The following represents the mapping of the Kernel attributes to their corresponding entities.

-----------------

DIAGRAM - Entity Mapping

-----------------


### Packaging

An important facet of the Kernel is that while it represents the core data elements supplied by D&B, it must be vetted and deemed universally beneficial to Microsofts wider customer base. That said, the elements that Microsoft deem universal will be incorporated into the core entities and ultimately managed by Microsoft.
Any elements considered too narrowly focused to D&B customers and hence proprietary, will still be delivered in to the Kernel, but will be packaged and managed by D&B.

The attributes listed above define the base characteristics of an attribute for an entity along with an indicator as to who will be responsible for it. Another important consideration is that attributes in to the CDS entities are considered additive. This means that once made available to customers via the CDS, it is understood that they will not be removed in the future. This implies that it is easier to add new value over time and adding too many elements early on have the potential to promote breaking-change if D&B believes they should be removed at a future point in time.


## FLOWS
Microsoft Flow is a product to help enterprise customers set up automated workflows between their favorite apps and services to synchronize files, get notifications, collect data, and more.

Flows are individually managed orchestrations that start with a trigger and result in one or more actions. Additional workflow features support such capabilities as conditional logic, approvals etc, some of which will be leveraged by D&B.

An integral part of the alliance is the delivery mechanism of the Kernel data to the CDS itself along with its on-going maintenance. This will be handled through flows. An important distinction between flows and templates are that templates are predefined flows that serve as the starting point of a flow. Once a flow is generated from a template (or started from scratch), a flow may add or remove any or all of the workflow steps defined within.

D&B will develop and manage a series of Flow templates that will serve as the mechanism for matching and enriching entities in the CDS. One ore more templates will be released to satisfy the supporting use cases.

### Match & Append

#### Initial, One-Time Bulk

#### On-Insert

#### On-Update

### Packaging


## CONNECTOR

### Overview

### Authentication

### Authorization

### Actions

#### Match
The match flow/template will be responsible for detecting change (triggered) on the Account entity and performing a Direct+ Plus match.

The match action on the connector will support all of the available inputs to the current Direct+ API service. The supported attributes include;

##### Firmographic Attributes
* **name** - primary name of the account
* **inLanguage** - An IETF BCP 47 code value that defines the language to be used to perform the match
* **duns** - A 9-character numeric string identifying the entity by its D&B assigned D-U-N-S number.
* **registrationNumber** - The number assigned by an external body or by D&B that either uniquely identifies or helps to identify an organization.
* **registrationNumberType** - A unique code assigned by D&B to identify the type of registration number.
* **streetAddressLine1** - Up to 70 characters of the first line of the entity's street address.
* **streetAddressLine2** - Up to 70 characters of the second line of the entity's street address.
* **countryISOAlpha2Code** - The 2-letter country code, defined by the International Organization for Standardization (ISO) ISO 3166-1 scheme identifying the country of the entity.
* **postalCode** - Up to 10 characters of the identifier used by the local country's postal authority to identify where the address is located.
* **addressLocality** - 1 to 50 characters that identifies the city, town, township, village, borough, etc. where the entity is located.
* **addressRegion** - The name of the locally governed area that forms part of a centrally governed nation to identify where the address is located.
* **addressCounty** - The name of the county in which this address is located.
* **telephoneNumber** - Up to 32 characters of the telephone number--the sequence of digits used for voice communication with the entity. This sequence of digits includes the area code or city code and domestic dialing code.
* **url** - A URL used to identify an entity by its email domain.
* **email** - An email address used to identify an entity by its email domain.

##### Metadata
* **customerBillingEndorsement** - Text that is filled in by customer and commonly contains requesting individual or department name, or customer's own account/reference number and/or name for the case on which the product was provided. This text is a reference used during the billing process.
* **customerReference** - A free form reference string provided by the customer to be linked to the product in order to support subsequent order reconciliation.
* **candidateMaximumQuantity** - The maximum number of results to be returned.
* **confidenceLowerLevelThresholdValue** - The lowest confidence level for entities returned in the response.
* **exclusionCriteria** - Provides the ability to exclude entities based on several properties.
* **isCleanseAndStandardizeInformationRequired** - Indicates if the cleanse and standardize information should be returned with the response.

#### Append


#### Extended Match (Match & Append)

### Packaging

## APPLICATION ECOSYSTEM

### Overview

### PowerApps

### Power BI

### Dynamics CRM & ERP

# Customer Onboarding


# Trial Access


# Self-Service

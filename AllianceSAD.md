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

---

DIAGRAM - Ecosystem Overview

---

The CDS will be the primary catalyst for initiating the request for data within its store to be cleaned, matched and appended. This will be performed in concert with Microsofts workflow engine, Flow. Flow will orchestrate the D&B actions to match and append through workflow definitions known as flows.
Flows are activated via a trigger. The primary triggers for the D&B related flows will be from the account entity within the CDS. Each time an account is created or updated, an associated flow (designed, released and managed by D&B) will determine if it needs to perform a match and/or an append.

If deemed necessary, the actions (i.e. match, append) will connect to the Direct+ APIs through a pre-configured connection (environment instance of a connector). The actions on the connection are responsible for making the calls to Direct+, marshaling the response and any additional exception handling.

----

DIAGRAM - Flow Overview

---

Once the account has been decorated with firmographic data, the platforms listed above will have immediate access to perform any number of value-added capabilities ranging from;
* Reporting
* Analytics
* Business based functions (i.e. field automation, segmentation etc.)
* Workflows
* Logic based functions (i.e. lead scoring, routing, alignment etc.)

The goal of the alliance is to provide customers and partners the ability take immediate advantage of D&Bs data throughout the Microsoft ecosystem, realizing benefits not previously afforded to them. Furthermore, it establishes a baseline that allows them to take advantage of D&Bs broader set of business data and those of its partner network.

## GO-TO-MARKET
TBD - definition around the sales model will help drive product implementation strategy.

# Solution
While the ecosystem covers a lot of ground and the realized benefit of this solution is even greater, this section will cover the key aspects of the solution.

## KERNEL
The Kernel is the branded packet of data that represents the entry-level dataset. It is a subset of the CMPELK product from Direct+ and has been curated by folks from both Microsoft and D&B to ensure the minimum set provides the appropriate level of value.

### Attributes

Following are the attributes that have been identified for the Kernel. Note these will be mapped from the Kernel directly to the BusinessProfile entity; an entity that relates to a variety account types within the CDS (i.e. Organization, Partner, Supplier etc.).

**TBD** - Finalize list of attributes including description and data type.


### Picklists
Lists-of-Values or picklists as defined in the CDS, represent a valid, predefined set of values (with display text). While no current physical limitation within CDS, the general guideline is lists containing less than 200 potential values would be defined as Picklists while those that are larger would be modeled as a Lookup.

**TBD** - capture list of Picklists, the values and display text, e.g. BusinessEntityType, RoleType etc. Review with MSFT if there is in I18N support that should be considered.

### Lookups
**TBD** - capture the list of lookups, ie ISD Country, SIC code etc.

### Entity Mapping
The following represents the mapping of the Kernel attributes to their corresponding entities.

---

DIAGRAM - Entity Mapping

---


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
The match and append flow is at the center of the integration strategy for D&B and the CDS. The flow will handle a series of triggered events from; initialization in the environment, on insert of new account and on update of existing account. These have been further refined below.

#### Initial, One-Time Multi-Process
**TBD** - Gather additional details from Clay on what he is authoring on our behalf here.

#### On-Insert
**TBD** - document trigger and if this is a separate flow or if it s configured in to the same flow.

#### On-Update
**TBD** - document trigger and if this is a separate flow or if it s configured in to the same flow.

#### Sync Entities
**TBD** - review approach to synchronizing the BusinessProfile and associated entities such as Account/Organization/Partner etc.

### Monitoring
A key component to the accuracy and relevancy of data will  be the ability for D&B to provide updates for a managed set of D-U-N-S. It is anticipated that monitoring will be utilized for this purpose.

The approach will be to enhance the match & append flow to transactionally register each newly managed D-U-N-S. Additionally, there will be a new flow will be created, based on a web-hook style trigger to receive each notification and perform the necessary updates in to the CDS.

Due to timing of the MVP and current limitations on the monitoring solution, it may be necessary to stage both the release and the approach itself. For these reasons we have broken out the strategy in to two phases, the first that is a non-monitoring approach, followed by the second which is based on monitoring.

#### Phase I
TBD - Non-monitoring

#### Phase II
TBD - Monitoring

### Packaging
Flow templates are the result of configured flows that are submitted to Microsoft and promoted as templates.

**TBD** review the packaging and release process. Include details on copy that will be viewed by developers. Capture all places where they will be visible and account for all copy.

## CONNECTOR

### Overview
The connector is a 3rd party vendors solution to connecting to its APIs through the Flow engine. A connector is considered the definition while a connection is the instance of a connector. It is designed to provide users a zero-coding experience to connecting and interacting with a predefined set of services.

In addition, the connector includes any authentication and authorization properties while exposing zero or more actions and triggers to be utilized in flows.

In a customers tenanted environment, an administrator or power user will define a new connection based on the connection specific details. As typical of other connectors, the D&B Direct Connector must include valid customer credentials. The D&B connector will require the following details;

* Consumer Key
* Consumer Secret


The connector will be made available within the PowerApps, Flow environments and subsequently supports some limited branding and marketing opportunities.


### Authentication
Microsoft Connectors support three primary means of authentication;

* Basic
* Token
* OAuth

Given the Direct+ approach to request a token before utilizing it (with an expiration of 24hrs), none of the three supported options will work without some level of modification.

There are merits for making change to support either of the three available means within Flow. Both Basic and Token will require effort on the API side (or via a proxy service), but in general are easier than OAuth. While OAuth is typically viewed as a persona based mechanism, there are advantages to leveraging this technique. One major advantage is we can begin the on-boarding process within the OAuth pages themselves.

Given the limited capabilities within the connector definition to forward prospects to an external link etc, it would be recommended that the connector ultimately support OAuth to rapidly facilitate new customer acquisition.

#### OAuth Requirements
**TBD** - Review OAuth requirements for sign-in and sign-up.

### Authorization
As Microsoft customers are required to be D&B customer in order to utilize the connector and its underlying services, authorization to the data they contain are equally important.

While it is not full understood what packets of data will be made available to CDS customers, it is clearly understood that there will be additional up-sell opportunities. These will most likely be modeled around the D&B lines of businesses - but not required. For this intent, how the data is authorized for the customer must be accounted for during initial implementation.

Another important facet of authorization is that it would be expected in application development that customers will have some level of interaction with the core Direct+ services directly. Given CMPELK is reduced as a subset for the Kernel, customers accessing the Direct+ services would provide them access to the greater set.

To facilitate these use cases, it is required that Direct+ model additional products such as the following;

* **KNLCMP** - Kernel data product consisting of the base company firmographics
* **KNLSMS** - Kernel plus Sales & Marketing business data
* **KNLRSK** - Kernel plus Risk business data

This is by no means the definitive list. It does however represent what is anticipated over the near to mid term phases of the alliance.


### Actions
Actions provided by the connector should remain as close to those currently supported by Direct+, with the exception of the attributes. This therefore states that while actions are currently defined by the flows that have been identified, they should not necessarily narrow focus whereby they prohibit other typical use cases by the same services.

Examples of use cases leveraging the same connector actions may include future support for multiple candidates for data stewardship. Further work is required and this guideline should be considered when modifying the actions.

The initial set of actions required to support the initial flow use cases include;
* Match
* Append (with custom product or subset of CMPELK)


#### Match
The match flow/template will be responsible for detecting change (triggered) on the Account entity and performing a Direct+ Plus match.

The match action on the connector will support all of the available inputs to the current Direct+ API service. The supported attributes include both Firmographic attributes and Metadata based attributes;

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

### Lifecycle & Versioning


## APPLICATION ECOSYSTEM

### Overview

### PowerApps

### Power BI

### Dynamics CRM & ERP

# Customer Onboarding


# Trial Access


# Self-Service

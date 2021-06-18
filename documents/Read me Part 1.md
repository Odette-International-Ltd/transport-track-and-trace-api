# **Automotive Supply Chain REST API**

VDA 4998 / Odette OA01 Part 1

Version 1.0, June 2021

**Summary** 

This Recommendation describes how to define and implement standardised REST-API interfaces for collaboration within the automotive industry and between the automotive industry and their logistics service providerspartners. 

Part 1 of the recommendation focusses on technical rules common to all processes. 

Part 2 describes the data model and functionality for the use of REST API in transport processes as an extension to established EDI data exchange processes. 

 **Disclaimer** 

The VDA Recommendations are recommendations that may be freely adopted by anyone. Users are responsible for correct implementation of the recommendations as required on a case-by-case basis. 

The recommendations take into account the prevailing technology at the time of publication. Use of the VDA Recommendations does not absolve anyone from responsibility for his/her own actions, and all users act at their own risk. Liability of VDA and those involved in drafting of VDA Recommendations is excluded. 

Please note: This is a copy of the original VDA/Odette recommendation. The official versions are available at www.vda.de and www.odette.org . 

|           |                                                              |
| :-------- | ------------------------------------------------------------ |
| Publisher | Verband der Automobilindustrie e.V. (VDA)  <br />Behrenstrasse 35, 10117 Berlin <br />www.vda.de <br />This recommendation was developed by AK SID together with an Odette project group. |
| Copyright | Odette International & Verband der Automobilindustrie e.V. (VDA) <br />Reprint, also in extracts, is only permitted, if the source is stated. Copyright |
| Version   | Version 1.0, June 2021                                       |

If you notice any errors, omissions or ambiguities in these recommendations, please contact VDA without delay so that these errors can be rectified. 



# 1. Introduction 

## 1.1 Purpose and Scope 

Modern supply and production processes require a close integration between involved partners. Although a variety of classic EDI (namely UN/EDIFACT) and XML-messages are available and cover many processes and steps, the currently available infrastructure often does not satisfy the demand for transparency and flexibility. 

With the technology of REpresentational State Transfer (REST) Application Programming Interfaces (API) there is an opportunity to enhance and amend currently available systems in a lightweight and , flexible, and state-of-the-art way. 

However, if these enhancements are defined and designed by the business partners individually, it is very likely that the variety of used data structures and implementations increases complexity instead of decreasing it. 

With this recommendation the issuing organisations lay out the rules for a standardised and harmonised approach so that implementation of such REST API is simple, scalability is supported, and hence the benefits are maximised. 

## 1.2 Conventions 

This document adheres to the use of key words 

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” as described in RFC 2119 (https://www.ietf.org/rfc/rfc2119.txt)-.-- 

## 1.3 Licence model of technical artefacts 

The technical artifacts are published under the General Public License V3.0: 

https://www.gnu.org/licenses/gpl-3.0.en.html 

## 1.4 Governance 

The technical artefacts published in connection with this recommendation follow the governance model suggested by ED3.org

(https://edi3.org/governance/). 

In particular, the following development status levels are used: 

| Status     | Definition                                                   | Usage                                                        |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| RAW        | Every new specification or major version starts with raw status | experimental use only                                        |
| DRAFT      | When a specification is completed and testable (i.e., it has a working test harness) then it becomes draft | suitable for beta testing                                    |
| STABLE     | When a specification has a successful third-party implementation (i.e., passes conformance test cases) then it becomes stable. | safe to implement in production systems                      |
| DEPRECATED | When a specification is superseded by a new major version then the previous major version is deprecated | may still be used in production but should not be used for new builds |
| RETIRED    | when a specification is obsolete and should no longer be used in any production deployment then it becomes retired | remains on this site for historical reference purposes       |

Versioning 

The following rules for versioning 

| Level | Description                                                  | Consequences                                                 |
| ----- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| MAJOR | a breaking change that requires a change to consumer systems | implementers must indicate version in URL path e.g. api.acme.com/v1/consignments |
| MINOR | a functional change or enhancement that is non-breaking (e.g., a new optional property in an API) | implementers must indicate minor version in the specification but not in URL path |
| PATCH | a non-functional change such as a documentation update       | no impact on implementers                                    |



# 2. Technical principles 

## 2.1 Functionality of RESTful API 

Although many applications claim to offer or support REST or RESTful services, there are differences in the level of support. 

According to Leonhard Richardson1 one can assess the maturity of REST services by this model:  

Include Figure

The layers mean: 

0 – just sending data (JSON) via HTTP POST – a.k.a. RESTless service since the very idea of REST services is not implemented at all. 1 – different resources are used and identified by different URI, However, only one HTTP method is used (typically POST). Other, enhanced HTTP protocol options such as header, return code or caching are not used. 
2 – Now HTTP methods are linked to operations, for instance GET for queries (read), POST for creation, PUT or PUSH for updates and DELETE for deletion (CRUD model). In addition, HTTP status codes are used to indicate the result of the operation (sometimes referred to as RESTalike). 
3 – In this level, hypermedia is introduced and used to build “self-explanatory” RESTful services. 

REST API in the automotive industry shall support at least level 2.  

## 2.2 HTTP methods 

### 2.2.1	POST

An empty POST operation mustshall be used, if the unique ID of the information object in question is to be generated and provided by the service providing system. The system creates an empty data structure and returns the identifier. The client system then uses this identifier as parameter in a PUT operation to provide the necessary data.
If the POST operation is used with an identifier of the information object, it transmits the complete data of the identified object. In the result of the operation a new object is created, and the transmitted data are stored in the service providing system.  

### 2.2.2	PUT

The PUT operation is always used with an identifier as parameter and transmits a complete data set of the identified object. The existing information object in the service providing system is completely replaced.

### 2.2.3	PATCH

The PATCH operation is always used with an identifier as parameter. The PATCH operation updates some fields in the identified information object, all other fields remain unchanged. 

### 2.2.4	GET

If the GET operation is used without an identifier, a list of identifiers of objects of the requested type stored in the service providing system shall be returned. The GET operation should be used with parameters for start and limit to divide the response in smaller, easier to process chunks of the complete list.
If the GET operation is used with an identifier as parameter, the complete data set of the identified object shall be returned by the service providing system (unless filter values are provided in the operation).

## 2.3	OpenAPI

“The OpenAPI Specification (OAS) defines a standard, programming language-agnostic interface description for REST APIs, which allows both humans and computers to discover and understand the capabilities of a service without requiring access to source code, additional documentation, or inspection of network traffic. When properly defined via OpenAPI, a consumer can understand and interact with the remote service with a minimal amount of implementation logic. Similar to what interface descriptions have done for lower-level programming, the OpenAPI Specification removes guesswork in calling a service.” 
REST API in the automotive industry shall be described and published in OpenAPI format (current version: 3.1, 2021).

## 2.4	Name and design rules

The automotive REST API recommendation adheres to the UN/CEFACT OPEN 3.0 DESIGN RULES.
Code values SHALL be all CAPITALS, or short integer numeric values (e.g. 123) or a combination of CAPITALS and digits. Where context specific code lists are defined, they SHOULD be created as English words, if necessary, separated by underscores.
Examples: TRUCK, ARRIVAL_DATE 

# 3	Architecture and data structures

## 3.1	Architectural considerations

On a pure technical level, a REST API provides – compared to traditional EDI communication infrastructure – a lightweight and more quickly to implement means to access an IT system and store data into or retrieve data from that system.
The system providing the REST API (hence receiving, storing, providing information) is then the service provider (server) and the system accessing the server via REST API is the service consumer (client).
Given the complexity of contemporary supply chains, many partners are involved with their IT systems and a variety of architectural flavours can be deployed. The three main variants are described in the following subchapters.

### 3.1.1	One central service provider


Figure 2

In this concept, one central application provides the REST API and all involved partners use this system to store and update their relevant data (information objects) and respectively retrieve it.
This central system could be provided, for instance, by a specialised IT company.
In this architecture all relevant information must be included in the information objects (or provided separately) to generate a complete digital twin or the physical world. If, for instance, the ship-from provides the details of a consignment for instance, the consignment item details must be included in the consignment data structure completely or transmitted separately to the service providing system, if relevant for the business process. 

### 3.1.2	Several interconnected service providers

Since many partners are involved in the supply chain, it is unlikely that only one system acts as the service provider and all the other systems as the consumer.
One rather finds a situation, where many partners operate systems that fulfil both roles, acting as consumer and as provider.
In such a system it is possible to limit the content of the information objects: all objects, for which details are retrievable from a separate service provider, only need to be identified in a way that the details can be gathered separately once they are needed (linked data principle).

Figure 3

### 3.1.3	Information hub architecture

When many service providers are interconnected in a peer-to-peer fashion, the communication setup can be complex and challenging. Therefore, dedicated IT platforms offer a hub and spoke architecture. The advantage for participants: they only need to connect to one system physically while getting virtual access to a whole network. The disadvantage: while direct connections between service provider and consumer often enable synchronous interactions, the hub and spoke architecture most likely may also use asynchronous communication.
Therefore, another layer in the data structure for messaging (i.e., an envelope-structure with sender and receiver information) is necessary and the Rest API intrinsic http response codes are only related to the communication between the hub and one spoke, for end-to-end responses another information artifact is necessary.

Figure 4

## 3.2	Object identification

To store and retrieve information objects in several distributed systems and to avoid the necessity to assign separate identifiers in each local system, they must be identified with globally unique identifiers.
There are several options available, among them:

1. Identification in compliance with ISO 15459XXXX / ANSI MH10.8.2 
   Here, the uniqueness is achieved by using globally unique company identifiers and serial numbers issued by the specified company. This principle is already used in various situations.
   Examples
   O0177A00100 – identifies Odette International Ltd. in the Odette Identification system
   1JUN498765432000001234 – Identifies an innermost package, serial number assigned by a company registered at D.U.N.S. with the number 498765432.

2. Type I UUID:
   An identifier created by concatenation of a timestamp and the MAC address of the creating system.
   Example: 470868c1-8194-4d22-8a7e-2a10144ae05d
   This identification scheme is widely used in software systems to identify e.g. records or other information objects for pure technical reasons. 
   Although usable for REST API interfaces as well, this kind of identification can be rather inconvenient in practical terms.

3. Uniform Resource Identifier – URI
   URI in conformance with RFC 3986 use a scheme identifier, an authority identifier, and a 
   path for identification of objects.
   Very commonly used are URL and URN sub-types of URI.
   a. URN uses a combination of a namespace identifier and a namespace specific string to
   identify objects, e.g. urn:ISBN:3-8273-7019-1 to identify a book.
   b. URL – Uniform Resource Locator identifies and locates a resource specifying a scheme,          an authority, and a path, e. g. https://api.mycompany.com/orders/12345.
   URL can also be used for queries like https://api.mycompany.com/orders?number=12345

In the context of this recommendation unique identification as described in 1. and 3.b. are the preferred identification schemes. However, if 3.b. is used with http or https scheme, the identified object shall be accessible to other systems via REST API. 

## 3.3 Modelling principles

As stated above, this recommendation is based on UN/CEFACT RDM2API methodology. The UN/CEFACT Core Component Library contains numerous contextualised Aggregate Business Information Entities (ABIE) for use in various business contexts and scenarios. Various levels of aggregation are used to build information models up to complete business documents.
If an object contains several associations to the same component object, which represent different semantic meaning, there are two types of associations available and used:

- An association class, using an attribute with a value list of applicable qualifiers (e.g. Party Role Code, Event Type Code etc.).

- Explicitly named associations to the component object (e.g. Buyer Party, Seller Party, Estimated Event, Actual Event).
  In the context of this recommendation type the option 1 is preferred and should be used, to allow semantic extensions to existing data structures without the necessity to considerably extend the programming code of existing implementations.  



## 3.4	Semantic validation

The applied modelling principle allows utmost flexibility of implementation scenarios and process orchestration. The downside of this methodology: the status information of attributes in the information objects apart from identifiers is mostly optional. For semantic validation it is often necessary to check if specific attributes are available because otherwise the information object cannot be processed correctlyproperly.
It is recommended to add an implementation specific validation layer when using the OopenAPI files provided in the scope of this project for implementations.
This validation can be done in several ways, of course. However, a very simple and straightforward way would be to use JSON sSemantic vValidationor through schematron techniques (https://www.npmjs.com/package/jsontron) on the data received. The output of this validation process can be used as error description in the response, should the validation fail.

# 4	Security

Depending on the business process and confidentiality of data content in a business environment various security features may be applicable or required:
•	Data encryption while in transit over the public internet
•	IP Whitelisting of REST API Consumer Systems (applicable for systems with fixed IP)
•	IP Whitelisting of REST API Service Provider Systems (applicable for systems with fixed IP)
•	Server Authentication of REST API Service Provider
•	Client Authentication of REST API Consumer
•	Authentication between REST API gateway and back-end system
•	Authentication between consumer and REST API Publisher (API Gateway or Firewall)
•	And more …

## 4.1	Server Authentication and Transport Security

The transport of business data via public internet is vulnerable to interception, tempering and other unwonted activities of “man in the middle” unless security measures are taken.
Therefore, the following rules apply:
•	ALL transactions MUST occur over HTTPS using at least the minimum secure version of TLS (currently TLS 1.2).
•	ALL certificates must be SHA256 with minimum key length of 2048 bit.
•	ALL publicly accessible endpoints MUST use a Digital Certificate that has been signed by an approved, i.e. trusted Certificate Authority (CA). It is recommended to use Certificates of CAs listed on Odette’s Trust Service Status List (TSL) for secure data exchange (https://www.odette.org/TSL/TSL_OFTP2.XML).
•	Endpoints facing to internal systems MAY use self-signed Digital Certificates.
•	Do not redirect HTTP traffic to HTTPS - reject these requests.
•	Unused HTTP methods SHOULD be disabled and return HTTP 405.
•	ALL requests must be validated.

## 4.2	Application security

One way to authenticate a client system (i.e. ensure the clients identity) is to use Client Authentication in the TLS protocol. In this case not only the server uses a security certificate but also the client. Client Certificates must also be issued by a trusted CA as well or by the service provider itself. A trusted CA certificate is preferable, since it can be used with many service providers (unless the service provider itself is member of the trust listTSL).
The application layer offers several options for identification and authorisation.
Basic Authentication:
The client uses user-ID and a password.
API-Key:
An asymmetric key, issued by the REST API Service Provider, is used to identify the client contacting the service provider.
OAuth:
Within OAuth infrastructure the responsibility for identification and authorisation is delegates to a third-party. The third-party issues tokens, which allowgain the client access to the service. By these means an SSO-principle can be established and through it access can be granted to many services offered by different providers. If even more security is required through authentication, the open Id Connect standard provides a means of combining OAuth 2.0 with ID tokens.
To be compliant with this recommendation, at least one of the above mentionedabove-mentioned features must be used to ensuregrant security and confidentiality of data exchanged through REST API services.  
 

# 5	Communication flow

## 5.1	Pull principle

Use case diagram einfügen
In communications following the Pull principle the consumer contacts the service provider and requests information. This is realised via HTTP GET operation. 

Explanation:
1.	The user contacts the server providing the service with a GET request and a URL, which tells the server, what kind of information is requested. In the call the user credentials are included.
2.	The server’s user management checks the identity and whether the user is entitled to receive the requested information.
3.	If the result of step 2 is positive, the request is passed through to the actual web service (API).
4.	The server retrieves the requested information from the backend system.
5.	The information is returned to the requester in the HTTP response (as a JSON structure).   
    Example:
    A potential user wants to know the details of a particular shipment with the ID 26KODA0010112345678.
    The user initiates this with a GET operation:
```
    curl -X 'GET' \
    'https://virtserver.someapi.com/vda_odette_ttt/V1/consignments/26KODA0010112345678' \
    -H 'accept: application/json' \
    -H 'Authorization: Basic VGVzdHVzZXI6dGVzdHBhc3N3b3Jk'
```

Request URL:
https://virtserver.someapi.com/vda_odette_ttt/V1/consignments/26KODA0010112345678
If the shipment is found, the server returns a HTTP code 200 (OK) and a JSON data structure describing the shipment:Rolands Bild einfügen

JSON code  	
{	
 "ID": {	
    "content": "26KODA001012021123456"	##Shipment ID (primary key)
  },	
  "ConsignorAssignedID": {	
    "content": "26KODA001012021123456"	Shipment ID 
  },	
  "GrossWeightMeasure": {	
    "content": 15000,	15000 kg gross weight
    "unitCode": "KGM"	
  },	
  "NetWeightMeasure": {	
    "content": 14000,	14000 kg net weight
    "unitCode": "KGM"	
  },	
  "ActualTransportStatus": {	
    "content" : "DEPARTED",	Current status: departed
    "listAgencyID": "10"	
  },	
  "SpecifiedLogisticsTransportMovement": [	
    {	
      "ID": {	
        "content": "JOURNEY123"	Journey ID
      }	
    }	
  ],	
  "SpecifiedTradeDeliveryTerms": {	
    "DeliveryTypeCode": {	
      "content": "EXW",	Delivery terms
      "listAgencyID": "6"	
    },	
    "Description": {	
      "content": "Ex work"	
    },	
    "RelevantTradeLocation": {	
      "ID": {	
        "content": "BER-BER",	Location related to delivery terms
        "schemeAgencyID": "6"	
      },	
      "Name": {	
        "content": "Berlin",	
        "languageID": "de"	
      }	
    }	
  },	
  "RelatedEventTransportEvent": [	Reference to the transport event 
    {	reporting the departure
      "ID": {	
        "content": "3421-1234-2145-98765"	The detail of the transport event can be retrieved using this ID
      },	
      "TypeCode": {	
        "content": "ACTUAL",	
        "listAgencyID": "10"	
      }	
    }	
 ],	
}	
Praktisches Beispiel dokumentieren 
5.2	Push principle
Use case diagram einfügen
Activity diagram ?
In communications following the Push principle the consumer contacts the service provider and pushes information onto the server
HTTP operations POST, PUT, PATCH are suitable for this process. DELETE falls into this category as well, but for transparency reasons information once provided SHALL NOT be deleted, rather invalidated by a change of status.

Explanation:
1.	The TMS of the client starts using the API to update information stored on the server. 
2.	The client system (web service consumer) initiates the call and provides credentials, the identification of the object, the operation, and the data to be stored.
3.	The server’s user management checks the identity and whether the user is entitled to send information.
	If the result of step 2 is positive, the request is passed through to the actual web service (API).
4.	The server stores the requested information into the backend system.
5.	Upon completion the HTTP response code is returned to the requester.  
6.	The successful completion of the operation is reported to the client’s backend system.

Example:
A potential user wants to add the customs assigned movement reference number to the details of shipment with the ID 26KODA0010112345678.
The user initiates this with a PATCH operation and provides the data to be added (or changed):
Rolands Bild einfügen
Praktisches Beispiel dokumentieren 
curl -X 'PATCH' \
  'https://virtserver.someapi.com/vda_odette_ttt/V1/consignments/26KODA0010112345678' \
  -H 'accept: application/json' \
  -H 'Authorization: Basic VGVzdHVzZXI6dGVzdHBhc3N3b3Jk' \
  -H 'Content-Type: application/json' \
  -d '{
  "CustomsID": {
    "content": "MRN085-2021"
  },
}'
If the operation is successful (the request was valid and could be processed), the server answers with code 200 – OK and the ID of the consignment, the update has been applied to:
{
  "ReturnedID": {
    "content": "26KODA0010112345678"
  }
}

## 5.3	Subscription

A user may want to be informed when information of specific information objects has changed.
There is the option of regularly issue a GET request, receive the data and compare to the locally stored data, if something has changed. The disadvantage of this method is obvious: if nothing has changed, unnecessary traffic is created and may slow down the server. Service providers may establish limits, how often in a period a client can issue a request. Worst case, the number is exhausted before a change happened and the retrieval of potentially important information will be delayed..
The alternative is to establish subscriptions. In this case, the service provider must offer callbacks. The client can then subscribe to certain events and will receive information that something has happened (consignment status has changed, for example). This information would trigger a pull process. This way GET operations are only conducted when they are useful.
On the other hand, the client system must offer a URL where to send this trigger information, i.e., must function as a server as well, which is always on-line.
If that cannot be guaranteed, it is recommended to add a messaging component to the infrastructure at the service provider to store “undeliverable” messages until the remote system is available again Activity diagram 

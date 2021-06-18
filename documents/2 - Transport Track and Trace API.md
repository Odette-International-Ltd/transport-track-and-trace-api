## VDA 4998 Part 2/ Odette OA02

Version 1.0, June 2021

**Summary**

This Recommendation describes how to define and implement standardised REST-API interfaces for collaboration within the automotive industry and between the automotive industry and their partners.

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

If you notice any errors, omissions or ambiguities in these recommendations, please contact VDA without delay so that these errors can be rectified.

# 1	Introduction and Scope
This part of the recommendation specifies the functionality of a standardised API for Tracking and Tracing shipments on their way from the supplier / ship-from to the customer / ship-to.
It is intended to extend existing, mostly EDI-based systems and to gain more transparency and flexibility in often complex transport processes.

## 1.1	Typical information flow in a transport process
Figure 1 illustrates the typical information flow accompanying the transport process. Flows marked as API are to be added and shall be harmonised by this recommendation.
 
Figure 1
## 1.2	Functional scope of this specification
The API is designed toshall support track and trace operations during the transport execution phase (see also chapter 3.3.2). Optionally, the ordering phase may be supported by a transport capacity reservation.
A service provider provides an API interface to gather and provide T&T information on:
* Shipments along their complete movement in their area of responsibility / from ship from to ship to;
* Shipment items along their complete movement from ship-from to ship-to;
To achieve this goal, partners in the supply chain shall should be able to perform the following operations:
* Ship-from can provide information on transport events of shipments and shipment items (e.g. loaded);
* Means of transport (or carrier) can provide transport events with reference to a transport movement and/or shipment and/or shipment item;
* Ship-to can provide transport events of shipments and shipment items (e.g. unloaded);
* X-Dock can provide transport events of shipments and shipment items;
* Any authorised party can retrieve information on shipments and shipment items; 
Optional:
* Any authorised party can retrieve information on transport movements and used means of transport.
* A shipper can issue a transport capacity reservation with to a transport service provider. 
The API consumer must be able to link transport movements of means of transport to the shipment they want to track and trace.
## 1.3	Minimum viable product
As described in Part 1 of this recommendation, there are several architectural options to orchestrate communication between partners in the supply chain via API.
This version of the recommendation intends to define data structures, functions, and architecture for a minimum viable product (MVP), i.e. to support the above described information flow with minimal effort.
It assumes the Transport Service Providers (TSP) to be  as the main API service providers as well (although other parties MAY host this kind of service as well). In combination with other, independently available services to track transport means such as like trucks, vessels, aircrafts, and trains (out of scope of this project), this will enable transparency of the whole transport chain.
 
Figure 2

The following table describes the required functionality of the T&T API.
Operations marked with status M are mandatory, operations marked with O are optional, D stands for dependent.
 


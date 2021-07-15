# Create Shipment

This transaction stores the details of a shipment (consignment) in the system.
There are mainly two possible data sources:   
* The ship-from party can push the data in preparation of the loading process 
* The logistics service provider can extract the data from a transport order received earlier    

Data set:
Field | Value  
------|------   
Shipment ID: | 2KODA05303020210003 (in this example a globally unique ID assigned by ship-from is used)  
Ship-from ID: | A05303 (Odette ID A053, Sub-entity 03)   
Ship-from address: | 71 Great Peter Street, London, SW1P 2BN, GB
Loading location: | Dock 15
Ship-to ID: | 987654321 (D.U.N.S. number)  
Ship-to address: | Behrenstraße 35, Berlin, 10117, DE   
Unloading location: | Abladestelle 23   
Gross weight: | 15000 kg
Gross volume: | 18 m3
Number of TLU: | 10 (1.2 x 1.0 x 1.5 m each) 
TLU-ID: | 6J (master label) ODA05303000000001..ODA05303000000010    
    
It is assumed that the receiving system checks internally, whether or not the transport handling unit    
(THU, i.e. ConsignmentItem) records exist in the system.    
If yes, the ConsignmentID within each ConsignmentItem has to be checked/updated,   
if not, the records have to be created by the system itself and filled with the data provided in the Consignment data set.    

```

curl -X 'PUT' \
  'https://virtserver.swaggerhub.com/JoergWaltherOdette/vda_odette_ttt/1.0.0/consignments/2KODA05303020210003' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -H 'X-API-KEY: asdfgh' \
  -d '{
 "ID": {
  "content": "2KODA05303020210003"
 },
 "ConsignorAssignedID": {
  "content": "2KODA05303020210003"
 },
 "GrossWeightMeasure": {
  "content": 15,
  "unitCode": "TNE"
 },
 "GrossVolumeMeasure": {
  "content": 18,
  "unitCode": "MTQ"
 },
 "ConsignmentItemQuantity": {
  "content": 10
 },
 "StatusCode": {
  "content": "NO_STATUS"
 },
 "SpecifiedDeliveryTerms": {
  "DeliveryTypeCode": {
   "content": "EXW"
  },
  "Description": {
   "content": "Ex works"
  },
  "RelevantLocation": {
   "Name": {
    "content": "London"
   }
  }
 },
 "IncludedConsignmentItem": [
  {
   "ID": {
    "content": "ODA05303000000001"
   },
   "SequenceNumeric": {
    "content": 1
   },
   "GrossWeightMeasure": {
    "content": 1500,
    "unitCode": "KGM"
   },
   "GrossVolumeMeasure": {
    "content": 1.8,
    "unitCode": "MTQ"
   },
   "ConsignmentID": {
    "content": "2KODA05303020210003"
   },
   "LinearDimension": {
    "WidthMeasure": {
     "content": 100,
     "unitCode": "CMT"
    },
    "LengthMeasure": {
     "content": 120,
     "unitCode": "CMT"
    },
    "HeightMeasure": {
     "content": 150,
     "unitCode": "CMT"
    }
   },
   "OriginCountry": {
    "ID": {
     "content": "GB"
    }
   },
   "LogisticsLabelShippingMarks": [
    {
     "LogisticsLabel": {
      "ID": {
       "content": "6JODA05303000000001"
      },
      "LayoutTypeCode": {
       "content": "GTL3"
      },
      "SizeCode": {
       "content": "A5"
      }
     }
    }
   ]
  },
  {
   "ID": {
    "content": "ODA05303000000002"
   },
   "SequenceNumeric": {
    "content": 2
   },
   "GrossWeightMeasure": {
    "content": 1500,
    "unitCode": "KGM"
   },
   "GrossVolumeMeasure": {
    "content": 1.8,
    "unitCode": "MTQ"
   },
   "ConsignmentID": {
    "content": "2KODA05303020210003"
   },
   "LinearDimension": {
    "WidthMeasure": {
     "content": 100,
     "unitCode": "CMT"
    },
    "LengthMeasure": {
     "content": 120,
     "unitCode": "CMT"
    },
    "HeightMeasure": {
     "content": 150,
     "unitCode": "CMT"
    }
   },
   "OriginCountry": {
    "ID": {
     "content": "GB"
    }
   },
   "LogisticsLabelShippingMarks": [
    {
     "LogisticsLabel": {
      "ID": {
       "content": "6JODA05303000000002"
      },
      "LayoutTypeCode": {
       "content": "GTL3"
      },
      "SizeCode": {
       "content": "A5"
      }
     }
    }
   ]
  }
 ],
 // And so on for all 10 THU
 "ConsignmentParty": [
  {
   "ID": {
    "content": "A05303",
    "schemeAgencyID": "10"
   },
   "Name": {
    "content": "Automotive Supplier Ltd."
   },
   "RoleCode": {
    "content": "SF"
   },
   "PostalAddress": {
    "PostcodeCode": {
     "content": "SW1P 2BN"
    },
    "StreetName": {
     "content": "71 Great Peter Street"
    },
    "CityName": {
     "content": "London"
    },
    "CountryID": {
     "content": "GB"
    }
   }
  },
  {
   "ID": {
    "content": "987654321 ",
    "schemeAgencyID": "16"
   },
   "Name": {
    "content": "Vereinigte Fahrzeugwerke Berlin"
   },
   "RoleCode": {
    "content": "ST"
   },
   "PostalAddress": {
    "PostcodeCode": {
     "content": "10117"
    },
    "StreetName": {
     "content": "Behrenstraße 35"
    },
    "CityName": {
     "content": "Berlin"
    },
    "CountryID": {
     "content": "DE"
    }
   }
  }
 ],
 "LogisticsLocation": [
  {
   "ID": {
    "content": "Dock 15"
   },
   "TypeCode": {
    "content": "9"
   }
  },
  {
   "ID": {
    "content": "Abladestelle 23"
   },
   "TypeCode": {
    "content": "11"
   }
  }
 ],
 "HandlingInstructions": {
  "Description": {
   "content": "string",
   "languageID": "aa"
  },
  "DescriptionCode": {
   "content": "string"
  },
  "MaximumStackabilityWeightApplicableMeasure": {
   "content": 3000,
   "unitCode": "KGM"
  },
  "MaximumStackabilityApplicableQuantity": {
   "content": 3
  }
 }
}   
```   
The system is expected to return code 201 "Created" since the Consignment object did not exist before   
in the database and had to be created with the provided ID as key (see also the comments on PUT in the yml file).   


# Use Case Transport Capacity Reservation
Use-Case |	Order transport capacity at a specified LSP for a specified contract relation  
---------|--------------------------------------------------------------------------------
Proposed by|	VDA PG API          
Proposed on|	11.09.2020         
Description|	In certain business scenarios it is sufficient to order transport capacity (loading meters, volume, weight) for a transport rather than specify the complete shipment.     
Actors|	Ship-from, LSP, optional: copy to ship-to / transport ordering party        
Pre-condition|	Contractual relationship between the transport ordering party and identified LSP    
Post-condition|	Confirmation      
Functions|	Create, Update, Read    
Process|	Sender: ship-from, Receiver: LSP,	Opt. Receiver: ship-to, transport ordering party    
Alternative|	VDA 4933 T1 & T2 (transport order & confirmation)  resp. Odette pendants     
Motivation |	Automated, accelerated communication    
Frequency|	As necessary      
```JSON
{
  "ID": {
    "content": "string"
  },
  "TypeCode": {
    "content": "1",
    "listAgencyID": "6"
  },
  "IssueDateTime": {
    "content": "string",
    "format": "102"
  },
  "IssuerTradeParty": {
    "ID": {
      "content": "string",
      "schemeAgencyID": "1"
    }
  },
  "RecipientTradeParty": [
    {
      "ID": {
        "content": "string",
        "schemeAgencyID": "1"
      }
    }
  ],
  "APIPayload": {
    "ConsignmentItem": {
      "ID": {
        "content": "string"
      },
      "SequenceNumeric": {
        "content": 0
      },
      "TypeCode": {
        "content": "ZZZ"
      },
      "GrossWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "NetWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "GrossVolumeMeasure": {
        "content": 0,
        "unitCode": "CMQ"
      },
      "PackageType": {
        "content": "string",
        "languageID": "aa"
      },
      "ConsignmentID": {
        "content": "string"
      },
      "StatusCode": {
        "content": "ACCEPTANCE_REFUSED_BY_SHIP_TO"
      },
      "LinearSpatialDimension": {
        "WidthMeasure": {
          "content": 0,
          "unitCode": "CMT"
        },
        "LengthMeasure": {
          "content": 0,
          "unitCode": "CMT"
        },
        "HeightMeasure": {
          "content": 0,
          "unitCode": "CMT"
        },
        "DiameterMeasure": {
          "content": 0,
          "unitCode": "CMT"
        }
      },
      "OriginTradeCountry": {
        "ID": {
          "content": "AD",
          "schemeAgencyID": "5"
        },
        "Name": {
          "content": "string",
          "languageID": "aa"
        }
      },
      "RelatedEventTransportEvent": [
        {
          "ID": {
            "content": "string"
          }
        }
      ],
      "LogisticsLabelLogisticsShippingMarks": [
        {
          "Marking": {
            "content": "string",
            "languageID": "aa"
          },
          "LogisticsLabel": {
            "ID": {
              "content": "string",
              "schemeAgencyID": "1"
            },
            "LayoutTypeCode": {
              "content": "ETI9"
            },
            "SizeCode": {
              "content": "A5"
            },
            "TechnologyCode": {
              "content": "BARCODE",
              "listAgencyID": "10"
            }
          }
        }
      ],
      "HandlingInstructions": {
        "Description": {
          "content": "string",
          "languageID": "aa"
        },
        "DescriptionCode": {
          "content": "string",
          "listAgencyID": "1"
        },
        "MaximumStackabilityWeightApplicableMeasure": {
          "content": 0,
          "unitCode": "KGM"
        },
        "MaximumStackabilityApplicableQuantity": {
          "content": 0
        },
        "MaximumStorageHumidityApplicableMeasure": {
          "content": 0,
          "unitCode": "P1"
        },
        "MinimumStorageHumidityApplicableMeasure": {
          "content": 0,
          "unitCode": "P1"
        },
        "InstructedTemperature": [
          {
            "MaximumValueMeasure": {
              "content": 0,
              "unitCode": "CEL"
            },
            "MinimumValueMeasure": {
              "content": 0,
              "unitCode": "CEL"
            },
            "TypeCode": {
              "content": "STORAGE",
              "listAgencyID": "10"
            }
          }
        ]
      }
    },
    "Consignment": {
      "ID": {
        "content": "string"
      },
      "ConsignorAssignedID": {
        "content": "string"
      },
      "ConsigneeAssignedID": {
        "content": "string"
      },
      "CustomsID": {
        "content": "string"
      },
      "CarrierAssignedID": {
        "content": "string"
      },
      "FreightForwarderAssignedID": {
        "content": "string"
      },
      "TradedParcelID": {
        "content": "string"
      },
      "LoadingSequenceNumeric": {
        "content": 0
      },
      "GrossWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "NetWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "GrossVolumeMeasure": {
        "content": 0,
        "unitCode": "CMQ"
      },
      "LoadingLengthMeasure": {
        "content": 0,
        "unitCode": "CMT"
      },
      "ChargeableWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "ConsignmentItemQuantity": {
        "content": 0
      },
      "StatusCode": {
        "content": "NO_STATUS"
      },
      "AssociatedReferencedDocument": [
        {
          "ID": {
            "content": "string"
          },
          "ReferenceTypeCode": {
            "content": "AAA",
            "listAgencyID": "6"
          },
          "LanguageID": {
            "content": "aa"
          },
          "FormattedIssueDateTime": {
            "content": "string"
          },
          "SubordinateLineID": {
            "content": "string"
          },
          "AttachedSpecifiedBinaryFile": [
            {
              "ID": {
                "content": "string"
              },
              "Title": {
                "content": "string",
                "languageID": "aa"
              },
              "FileName": {
                "content": "string",
                "languageID": "aa"
              },
              "URIID": {
                "content": "string"
              },
              "MIMECode": {
                "content": "string",
                "listAgencyID": "1"
              },
              "EncodingCode": {
                "content": "string",
                "listAgencyID": "1"
              },
              "CharacterSetCode": {
                "content": "string",
                "listAgencyID": "1"
              },
              "IncludedBinaryObject": {
                "content": "string",
                "format": "string"
              },
              "Access": {
                "content": "string",
                "languageID": "aa"
              },
              "Description": {
                "content": "string",
                "languageID": "aa"
              },
              "SizeMeasure": {
                "content": 0,
                "unitCode": "10"
              }
            }
          ]
        }
      ],
      "UtilizedLogisticsTransportEquipment": [
        {
          "ID": {
            "content": "string"
          },
          "CategoryCode": {
            "content": "AA",
            "listAgencyID": "6"
          },
          "CharacteristicCode": {
            "content": "1",
            "listAgencyID": "6"
          }
        }
      ],
      "SpecifiedLogisticsTransportMovement": [
        {
          "StageCode": {
            "content": "12",
            "listAgencyID": "6"
          },
          "ModeCode": {
            "content": "0",
            "listAgencyID": "6"
          },
          "ID": {
            "content": "string"
          }
        }
      ],
      "SpecifiedTradeDeliveryTerms": {
        "DeliveryTypeCode": {
          "content": "1",
          "listAgencyID": "6"
        },
        "Description": {
          "content": "string"
        },
        "PartialDeliveryAllowedIndicator": {
          "content": "string"
        },
        "RelevantTradeLocation": {
          "ID": {
            "content": "string",
            "schemeAgencyID": "1"
          },
          "Name": {
            "content": "string",
            "languageID": "aa"
          }
        }
      },
      "SpecifiedSupplyChainReference": [
        {
          "TypeCode": {
            "content": "AAA",
            "listAgencyID": "6"
          },
          "ID": {
            "content": "string"
          }
        }
      ],
      "IncludedConsignmentItem": [
        {
          "ID": {
            "content": "string"
          },
          "SequenceNumeric": {
            "content": 0
          },
          "TypeCode": {
            "content": "ZZZ"
          },
          "GrossWeightMeasure": {
            "content": 0,
            "unitCode": "KGM"
          },
          "NetWeightMeasure": {
            "content": 0,
            "unitCode": "KGM"
          },
          "GrossVolumeMeasure": {
            "content": 0,
            "unitCode": "CMQ"
          },
          "PackageType": {
            "content": "string",
            "languageID": "aa"
          },
          "ConsignmentID": {
            "content": "string"
          },
          "StatusCode": {
            "content": "ACCEPTANCE_REFUSED_BY_SHIP_TO"
          },
          "LinearSpatialDimension": {
            "WidthMeasure": {
              "content": 0,
              "unitCode": "CMT"
            },
            "LengthMeasure": {
              "content": 0,
              "unitCode": "CMT"
            },
            "HeightMeasure": {
              "content": 0,
              "unitCode": "CMT"
            },
            "DiameterMeasure": {
              "content": 0,
              "unitCode": "CMT"
            }
          },
          "OriginTradeCountry": {
            "ID": {
              "content": "AD",
              "schemeAgencyID": "5"
            },
            "Name": {
              "content": "string",
              "languageID": "aa"
            }
          },
          "RelatedEventTransportEvent": [
            {
              "ID": {
                "content": "string"
              }
            }
          ],
          "LogisticsLabelLogisticsShippingMarks": [
            {
              "Marking": {
                "content": "string",
                "languageID": "aa"
              },
              "LogisticsLabel": {
                "ID": {
                  "content": "string",
                  "schemeAgencyID": "1"
                },
                "LayoutTypeCode": {
                  "content": "ETI9"
                },
                "SizeCode": {
                  "content": "A5"
                },
                "TechnologyCode": {
                  "content": "BARCODE",
                  "listAgencyID": "10"
                }
              }
            }
          ],
          "HandlingInstructions": {
            "Description": {
              "content": "string",
              "languageID": "aa"
            },
            "DescriptionCode": {
              "content": "string",
              "listAgencyID": "1"
            },
            "MaximumStackabilityWeightApplicableMeasure": {
              "content": 0,
              "unitCode": "KGM"
            },
            "MaximumStackabilityApplicableQuantity": {
              "content": 0
            },
            "MaximumStorageHumidityApplicableMeasure": {
              "content": 0,
              "unitCode": "P1"
            },
            "MinimumStorageHumidityApplicableMeasure": {
              "content": 0,
              "unitCode": "P1"
            },
            "InstructedTemperature": [
              {
                "MaximumValueMeasure": {
                  "content": 0,
                  "unitCode": "CEL"
                },
                "MinimumValueMeasure": {
                  "content": 0,
                  "unitCode": "CEL"
                },
                "TypeCode": {
                  "content": "STORAGE",
                  "listAgencyID": "10"
                }
              }
            ]
          }
        }
      ],
      "RelatedEventTransportEvent": [
        {
          "ID": {
            "content": "string"
          }
        }
      ],
      "ConsignmentParty": {
        "ID": {
          "content": "string",
          "schemeID": "string",
          "schemeAgencyID": "1"
        },
        "Name": {
          "content": "string",
          "languageID": "aa"
        },
        "RoleCode": {
          "content": "CA",
          "listAgencyID": "6"
        },
        "PostalTradeAddress": {
          "ID": {
            "content": "string",
            "schemeAgencyID": "1"
          },
          "PostcodeCode": {
            "content": "string"
          },
          "StreetName": {
            "content": "string"
          },
          "CityName": {
            "content": "string"
          },
          "CountryID": {
            "content": "AD",
            "schemeAgencyID": "5"
          },
          "CountryName": {
            "content": "string"
          },
          "CountrySubDivisionName": {
            "content": "string"
          }
        },
        "UniversalCommunication": [
          {
            "URIID": {
              "content": "string",
              "schemeID": "string",
              "schemeAgencyID": "1"
            },
            "ChannelCode": {
              "content": "AL"
            },
            "CompleteNumber": {
              "content": "string",
              "languageID": "aa"
            }
          }
        ]
      },
      "LogisticsLocation": {
        "ID": {
          "content": "string",
          "schemeAgencyID": "1"
        },
        "Name": {
          "content": "string",
          "languageID": "aa"
        },
        "TypeCode": {
          "content": "9",
          "listAgencyID": "6"
        },
        "CountryID": {
          "content": "AD",
          "schemeAgencyID": "5"
        },
        "CountrySubDivisionID": {
          "content": "string",
          "schemeID": "string",
          "schemeName": "string",
          "schemeAgencyID": "1",
          "schemeAgencyName": "string",
          "schemeVersionID": "string",
          "schemeDataURI": "string",
          "schemeURI": "string"
        },
        "PhysicalGeographicalCoordinate": {
          "AltitudeMeasure": {
            "content": 0,
            "unitCode": "MTR"
          },
          "LatitudeMeasure": {
            "content": 0,
            "unitCode": "DD"
          },
          "LongitudeMeasure": {
            "content": 0,
            "unitCode": "DD"
          },
          "LatitudeDirectionIndicator": {
            "content": "string"
          },
          "LongitudeDirectionIndicator": {
            "content": "string"
          },
          "SystemID": {
            "content": "string",
            "schemeAgencyID": "1"
          }
        }
      },
      "HandlingInstructions": {
        "Description": {
          "content": "string",
          "languageID": "aa"
        },
        "DescriptionCode": {
          "content": "string",
          "listAgencyID": "1"
        },
        "MaximumStackabilityWeightApplicableMeasure": {
          "content": 0,
          "unitCode": "KGM"
        },
        "MaximumStackabilityApplicableQuantity": {
          "content": 0
        },
        "MaximumStorageHumidityApplicableMeasure": {
          "content": 0,
          "unitCode": "P1"
        },
        "MinimumStorageHumidityApplicableMeasure": {
          "content": 0,
          "unitCode": "P1"
        },
        "InstructedTemperature": [
          {
            "MaximumValueMeasure": {
              "content": 0,
              "unitCode": "CEL"
            },
            "MinimumValueMeasure": {
              "content": 0,
              "unitCode": "CEL"
            },
            "TypeCode": {
              "content": "STORAGE",
              "listAgencyID": "10"
            }
          }
        ]
      }
    },
    "TransportMovement": {
      "StageCode": {
        "content": "1",
        "listAgencyID": "6"
      },
      "ModeCode": {
        "content": "0",
        "listAgencyID": "6"
      },
      "Mode": {
        "content": "string",
        "languageID": "aa"
      },
      "ID": {
        "content": "string"
      },
      "Information": {
        "content": "string",
        "languageID": "aa"
      },
      "CargoDescription": {
        "content": "string",
        "languageID": "aa"
      },
      "DangerousGoodsIndicator": {
        "content": "string"
      },
      "StatusCode": {
        "content": "ARRIVAL_COMPLETED",
        "listAgencyID": "6"
      },
      "UsedTransportMeans": {
        "TypeCode": {
          "content": "T01",
          "listAgencyID": "6"
        },
        "Type": {
          "content": "string",
          "languageID": "aa"
        },
        "ID": {
          "content": "string",
          "schemeAgencyID": "1"
        },
        "Name": {
          "content": "string",
          "languageID": "aa"
        }
      },
      "IncludedConsignment": [
        {
          "ID": {
            "content": "string"
          },
          "ConsignorAssignedID": {
            "content": "string"
          },
          "StatusCode": {
            "content": "NO_STATUS"
          }
        }
      ],
      "TransportPartyConsignmentParty": [
        {
          "ID": {
            "content": "string",
            "schemeID": "string",
            "schemeAgencyID": "1"
          },
          "Name": {
            "content": "string",
            "languageID": "aa"
          },
          "RoleCode": {
            "content": "CA",
            "listAgencyID": "6"
          },
          "PostalTradeAddress": {
            "ID": {
              "content": "string",
              "schemeAgencyID": "1"
            },
            "PostcodeCode": {
              "content": "string"
            },
            "StreetName": {
              "content": "string"
            },
            "CityName": {
              "content": "string"
            },
            "CountryID": {
              "content": "AD",
              "schemeAgencyID": "5"
            },
            "CountryName": {
              "content": "string"
            },
            "CountrySubDivisionName": {
              "content": "string"
            }
          },
          "UniversalCommunication": [
            {
              "URIID": {
                "content": "string",
                "schemeID": "string",
                "schemeAgencyID": "1"
              },
              "ChannelCode": {
                "content": "AL"
              },
              "CompleteNumber": {
                "content": "string",
                "languageID": "aa"
              }
            }
          ]
        }
      ],
      "RelatedEventTransportEvent": [
        {
          "ID": {
            "content": "string"
          }
        }
      ]
    },
    "TransportCapacityReservation": {
      "ID": {
        "content": "string"
      },
      "TransactionStatusCode": {
        "content": "CONFIRMATION_PENDING"
      },
      "IssueDateDateTime": {
        "content": "string"
      },
      "PositioningDateDateTime": {
        "content": "string"
      },
      "TransportMeansTypeCode": {
        "content": "T01",
        "listAgencyID": "6"
      },
      "TransportMeansNumberNumeric": {
        "content": 0
      },
      "GrossWeightMeasureMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "LoadingMetersMeasureMeasure": {
        "content": 0,
        "unitCode": "MTR"
      },
      "GrossVolumeMeasureMeasure": {
        "content": 0,
        "unitCode": "LTR"
      },
      "DeliveryTermsCode": {
        "content": "1"
      },
      "ContractReferenceID": {
        "content": "string"
      },
      "SpecialInstructions": {
        "content": "string",
        "languageID": "aa"
      },
      "SpecifiedPartyTradeParty": [
        {
          "IDID": {
            "content": "string",
            "schemeAgencyID": "10"
          },
          "Name": {
            "content": "string",
            "languageID": "aa",
            "languageLocaleID": "string"
          },
          "RoleCode": {
            "content": "OB",
            "listAgencyID": "6"
          },
          "PostalAddressTradeAddress": [
            {
              "ID": {
                "content": "string",
                "schemeAgencyID": "1"
              },
              "PostcodeCode": {
                "content": "string"
              },
              "StreetName": {
                "content": "string"
              },
              "CityName": {
                "content": "string"
              },
              "CountryID": {
                "content": "AD",
                "schemeAgencyID": "5"
              },
              "CountryName": {
                "content": "string"
              },
              "CountrySubDivisionName": {
                "content": "string"
              }
            }
          ],
          "UniversalCommunication": [
            {
              "URIID": {
                "content": "string",
                "schemeID": "string",
                "schemeAgencyID": "1"
              },
              "ChannelCode": {
                "content": "AA",
                "listAgencyID": "6"
              },
              "CompleteNumber": {
                "content": "string",
                "languageID": "aa"
              }
            }
          ]
        },
        {
          "IDID": {
            "content": "string",
            "schemeAgencyID": "10"
          },
          "Name": {
            "content": "string",
            "languageID": "aa",
            "languageLocaleID": "string"
          },
          "RoleCode": {
            "content": "OB",
            "listAgencyID": "6"
          },
          "PostalAddressTradeAddress": [
            {
              "ID": {
                "content": "string",
                "schemeAgencyID": "1"
              },
              "PostcodeCode": {
                "content": "string"
              },
              "StreetName": {
                "content": "string"
              },
              "CityName": {
                "content": "string"
              },
              "CountryID": {
                "content": "AD",
                "schemeAgencyID": "5"
              },
              "CountryName": {
                "content": "string"
              },
              "CountrySubDivisionName": {
                "content": "string"
              }
            }
          ],
          "UniversalCommunication": [
            {
              "URIID": {
                "content": "string",
                "schemeID": "string",
                "schemeAgencyID": "1"
              },
              "ChannelCode": {
                "content": "AA",
                "listAgencyID": "6"
              },
              "CompleteNumber": {
                "content": "string",
                "languageID": "aa"
              }
            }
          ]
        }
      ],
      "LogisticsLocation": [
        {
          "ID": {
            "content": "string",
            "schemeAgencyID": "1"
          },
          "Name": {
            "content": "string",
            "languageID": "aa"
          },
          "TypeCode": {
            "content": "9",
            "listAgencyID": "6"
          },
          "CountryID": {
            "content": "AD",
            "schemeAgencyID": "5"
          },
          "CountrySubDivisionID": {
            "content": "string",
            "schemeID": "string",
            "schemeName": "string",
            "schemeAgencyID": "1",
            "schemeAgencyName": "string",
            "schemeVersionID": "string",
            "schemeDataURI": "string",
            "schemeURI": "string"
          },
          "PhysicalGeographicalCoordinate": {
            "AltitudeMeasure": {
              "content": 0,
              "unitCode": "MTR"
            },
            "LatitudeMeasure": {
              "content": 0,
              "unitCode": "DD"
            },
            "LongitudeMeasure": {
              "content": 0,
              "unitCode": "DD"
            },
            "LatitudeDirectionIndicator": {
              "content": "string"
            },
            "LongitudeDirectionIndicator": {
              "content": "string"
            },
            "SystemID": {
              "content": "string",
              "schemeAgencyID": "1"
            }
          },
          "PostalTradeAddress": {
            "ID": {
              "content": "string",
              "schemeAgencyID": "1"
            },
            "PostcodeCode": {
              "content": "string"
            },
            "StreetName": {
              "content": "string"
            },
            "CityName": {
              "content": "string"
            },
            "CountryID": {
              "content": "AD",
              "schemeAgencyID": "5"
            },
            "CountryName": {
              "content": "string"
            },
            "CountrySubDivisionName": {
              "content": "string"
            }
          }
        }
      ]
    },
    "TransportEvent": {
      "ID": {
        "content": "string"
      },
      "TypeCode": {
        "content": "ACTUAL",
        "listAgencyID": "10"
      },
      "ReportedConditionTypeCode": {
        "content": "ACCEPTANCE_REFUSED_BY_SHIP_TO",
        "listAgencyID": "6"
      },
      "OccurenceDateTimeDateTime": {
        "content": "string"
      },
      "OccurrenceLogisticsLocation": {
        "ID": {
          "content": "string",
          "schemeAgencyID": "1"
        },
        "Name": {
          "content": "string",
          "languageID": "aa"
        },
        "TypeCode": {
          "content": "1",
          "listAgencyID": "6"
        },
        "CountryID": {
          "content": "AD",
          "schemeAgencyID": "5"
        },
        "CountrySubDivisionID": {
          "content": "string"
        },
        "PhysicalGeographicalCoordinate": {
          "AltitudeMeasure": {
            "content": 0,
            "unitCode": "10"
          },
          "LatitudeMeasure": {
            "content": 0,
            "unitCode": "DD"
          },
          "LongitudeMeasure": {
            "content": 0,
            "unitCode": "DD"
          },
          "LatitudeDirectionIndicator": {
            "content": "string"
          },
          "LongitudeDirectionIndicator": {
            "content": "string"
          },
          "SystemID": {
            "content": "string",
            "schemeAgencyID": "1"
          }
        }
      },
      "RelatedSpecifiedObservation": [
        {
          "ID": {
            "content": "string"
          },
          "Description": {
            "content": "string",
            "languageID": "aa"
          },
          "RelatedSpecifiedBinaryFile": [
            {
              "ID": {
                "content": "string"
              },
              "Title": {
                "content": "string",
                "languageID": "aa"
              },
              "FileName": {
                "content": "string",
                "languageID": "aa"
              },
              "URIID": {
                "content": "string"
              },
              "MIMECode": {
                "content": "string",
                "listAgencyID": "1"
              },
              "EncodingCode": {
                "content": "string",
                "listAgencyID": "1"
              },
              "CharacterSetCode": {
                "content": "string",
                "listAgencyID": "1"
              },
              "IncludedBinaryObject": {
                "content": "string",
                "format": "string"
              },
              "Description": {
                "content": "string",
                "languageID": "aa"
              },
              "SizeMeasure": {
                "content": 0,
                "unitCode": "4L"
              }
            }
          ],
          "ApplicableNote": [
            {
              "Subject": {
                "content": "string",
                "languageID": "aa"
              },
              "Content": {
                "content": "string",
                "languageID": "aa"
              }
            }
          ]
        }
      ],
      "ReportingMonitoringIOTDevice": [
        {
          "ID": {
            "content": "string"
          },
          "TypeCode": {
            "content": "string"
          }
        }
      ],
      "ReferencedTransportMovement": {
        "StageCode": {
          "content": "1",
          "listAgencyID": "6"
        },
        "ModeCode": {
          "content": "0",
          "listAgencyID": "6"
        },
        "ID": {
          "content": "string"
        },
        "UsedTransportMeans": {
          "TypeCode": {
            "content": "T01",
            "listAgencyID": "6"
          },
          "Type": {
            "content": "string",
            "languageID": "aa"
          },
          "ID": {
            "content": "string",
            "schemeAgencyID": "1"
          },
          "Name": {
            "content": "string",
            "languageID": "aa"
          }
        }
      },
      "ReferencedConsignment": [
        {
          "ID": {
            "content": "string"
          },
          "StatusCode": {
            "content": "NO_STATUS"
          },
          "IncludedConsignmentItem": [
            {
              "ID": {
                "content": "string"
              }
            }
          ]
        }
      ],
      "ReferencedConsignmentItem": [
        {
          "ID": {
            "content": "string"
          }
        }
      ]
    }
  }
}

```   


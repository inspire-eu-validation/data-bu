# Code lists

**Purpose**: Verify that code lists extensions can be accessed.

**Prerequisites**

**Test method**

* Verify that any code list extensions are publicly accessible via HTTP, i.e. inspect extensible code list values property elements. If a reference (@xlink:href) has a value that does not start with http://inspire.ec.europa.eu/codelist/, verify that a HTTP GET request to the URI retrieves a document. Otherwise report [brokenLink](#brokenLink).

This data theme currently has the following extensible code lists:

* [BuildingNatureValue](#BuildingNatureValue): http://inspire.ec.europa.eu/codelist/BuildingNatureValue

* [CurrentUseValue](#CurrentUseValue): http://inspire.ec.europa.eu/codelist/CurrentUseValue


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (3)

**Test type**: Automated

**Notes**

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
brokenLink <a name="brokenLink"/>  |  XML document '$filename', $featureType '$gmlid': The property '$propertyName' has a value '$value' that cannot be retrieved using HTTP. Every code list value must be made available in an online registry. 

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression      |Multiplicity   |Voidable
---------------------------------------------------------- | -----------------------|---------------|---------------------------------
BuildingNatureValue <a name="BuildingNatureValue"></a> | //schema-element(bu-core2d:Building)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:buildingNature/@xlink:href | 0..\* | Yes
CurrentUseValue <a name="CurrentUseValue"></a> | //schema-element(bu-core2d:Building)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href | 1 (0..\* for the parent element) | No

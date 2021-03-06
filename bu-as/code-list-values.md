# Code list values

**Purpose**: Verify whether all attributes whose value type is a code list take the values set out therein

**Prerequisites**

**Test method**

When an attribute has a code list as its type, verify that the values comply with the definitions and include the values set out in Annex II, III and IV of the Implementing Rule. To pass this test verify that any instance of an attribute:

* takes only values explicitly specified in the INSPIRE code list register when the code list‘s extensibility is 'none'.
* takes only a value explicitly specified in the INSPIRE code list register or shall take a value that is narrower (i.e. more specific) than those explicitly specified in the application schema when the code list‘s extensibility is 'narrower'.
* takes values explicitly specified in the INSPIRE code list register when the code list‘s extensibility is 'open' or if a value is not one of the values listed in the code list register check that any extensions do not overlap with the code lists that are defined in Annexes II, III and IV of the Implementing Rule and that all extensions conform to the requirements (This last check is a manual test).

The following checks are performed for every feature in the dataset, for the not extensible codelists:

* Check that all the [conditionOfConstruction](#conditionOfConstruction) elements has a xlink:href attribute pointing to a [valid value](#validValue1). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).

* Check that all the [elevationReference](#elevationReference), [heightReference](#heightReference), [lowReference](#lowReference),  [verticalGeometryReference](#verticalGeometryReference), [verticalGeometryReference3DBottom](#verticalGeometryReference3DBottom) and [verticalGeometryReference3DTop](#verticalGeometryReference3DTop) elements have a xlink:href attribute pointing to a [valid value](#validValue2). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).

* Check that all the [status](#status) elements has a xlink:href attribute pointing to a [valid value](#validValue3). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).

* Check that all the [horizontalGeometryReference](#horizontalGeometryReference) elements (if present) has a xlink:href attribute pointing to a [valid value](#validValue4). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).


| <a name="validValue1"></a> Valid values for xlink:href attribute of [conditionOfConstruction](#conditionOfConstruction) element are available in the INSPIRE Registry| 
| ---- | 
| ConditionOfConstructionValue: http://inspire.ec.europa.eu/codelist/ConditionOfConstructionValue | 

| <a name="validValue2"></a> Valid values for xlink:href attribute of [elevationReference](#elevationReference), [heightReference](#heightReference), [lowReference](#lowReference),  [verticalGeometryReference](#verticalGeometryReference), [verticalGeometryReference3DBottom](#verticalGeometryReference3DBottom) and [verticalGeometryReference3DTop](#verticalGeometryReference3DTop) elements are available in the INSPIRE Registry.| 
| ---- | 
| ElevationReferenceValue: http://inspire.ec.europa.eu/codelist/ElevationReferenceValue |

| <a name="validValue3"></a> Valid values for xlink:href attribute of [status](#status) element are available in the INSPIRE Registry| 
| ---- | 
| HeightStatusValue: http://inspire.ec.europa.eu/codelist/HeightStatusValue | 

| <a name="validValue4"></a> Valid values for xlink:href attribute of [horizontalGeometryReference](#horizontalGeometryReference) element are available in the INSPIRE Registry| 
| ---- | 
| HorizontalGeometryReferenceValue: http://inspire.ec.europa.eu/codelist/HorizontalGeometryReferenceValue | 


The following check is performed for every feature in the dataset, for the 'open' codelist:

* Check that all the [buildingNature](#buildingNature) elements has a xlink:href attribute pointing to a [pre-defined value](#preDefinedValue). If the check fails a manual check will be required asking to review the code list definition in order to verify that any extensions do not overlap with the code lists that are defined in Annexes II, III and IV of the Implementing Rule. If the check fails report [reviewCodeListValue](#reviewCodeListValue).

| <a name="preDefinedValue"></a> Pre-defined values for xlink:href attribute of [buildingNature](#buildingNature) element are available in the INSPIRE Registry| 
| ---- | 
| BuildingNatureValue: http://inspire.ec.europa.eu/codelist/BuildingNatureValue | 


The following check is performed for every feature in the dataset, for the 'narrower' codelist:

* Check that all the [currentUse](#currentUse) elements has a xlink:href attribute pointing to a [pre-defined value](#preDefinedValue1). If the check fails a manual check will be required asking to review the codelist definition in order to verify that any extensions do not overlap with the codelists that are defined in Annexes II, III and IV of the Implementing Rule. In particular, for the 'narrower' codelists the extended values shall refer to a parent value defined by the Implementing Rule. If the check fails report [reviewCodeListValue](#reviewCodeListValue).

| <a name="preDefinedValue1"></a> Pre-defined values for xlink:href attribute of [currentUse](#currentUse) element are available in the INSPIRE Registry| 
| ---- | 
| CurrentUseValue: http://inspire.ec.europa.eu/codelist/CurrentUseValue | 


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (1)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (3)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (1)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (2)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (3)
* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 6 (4)

**Test type**: Automated + Manual check (if required)

**Notes**

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
disallowedCodeListValue <a name="disallowedCodeListValue"/> | XML document '$filename', $featureType '$gmlid': The property '$propertyName' has a value '$value' that is not one of the allowed values listed at $codelist. Please note that the URIs of all code list values from the INSPIRE Registry shall be referenced using the http protocol. 
reviewCodeListValue <a name="reviewCodeListValue"/> | XML document '{filename}', {featureType} '{gmlid}': The property '{property}' has a value '{value}' that is not one of the pre-defined values in the INSPIRE data specification. The same value is used by {count} other features in the dataset, too. Extensions to the pre-defined values are allowed, but must not overlap with one of the pre-defined values and be consistent with the specification of the property. Please review the definition of the value. Please note that the URIs of all code list values from the INSPIRE Registry shall be referenced using the http protocol. 

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression				|Multiplicity       |Voidable
---------------------------------------------------------- | -------------------------------|-------------------|---------
conditionOfConstruction <a name="conditionOfConstruction"></a> | //schema-element(bu-core2d:Building)/bu-base:conditionOfConstruction/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:conditionOfConstruction/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:conditionOfConstruction/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:conditionOfConstruction/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:conditionOfConstruction/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:conditionOfConstruction/@xlink:href | 1 | Yes
elevationReference <a name="elevationReference"></a> | //schema-element(bu-core2d:Building)/bu-base:elevation/bu-base:Elevation/bu-base:elevationReference/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:elevation/bu-base:Elevation/bu-base:elevationReference/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:elevation/bu-base:Elevation/bu-base:elevationReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:elevation/bu-base:Elevation/bu-base:elevationReference/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:elevation/bu-base:Elevation/bu-base:elevationReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:elevation/bu-base:Elevation/bu-base:elevationReference/@xlink:href | 1 (0..\* for the parent element) | No
heightReference <a name="heightReference"></a> | //schema-element(bu-core2d:Building)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:heightReference/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:heightReference/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:heightReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:heightReference/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:heightReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:heightReference/@xlink:href | 1 (0..\* for the parent element) | Yes
lowReference <a name="lowReference"></a> | //schema-element(bu-core2d:Building)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:lowReference/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:lowReference/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:lowReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:lowReference/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:lowReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:lowReference/@xlink:href | 1 (0..\* for the parent element) | Yes
verticalGeometryReference <a name="verticalGeometryReference"></a> | //schema-element(bu-core2d:Building)/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:verticalGeometryReference/@xlink:href | 0..1 | No
" | //schema-element(bu-core2d:BuildingPart)/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:verticalGeometryReference/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:verticalGeometryReference/@xlink:href | 0..1 (1..\* for the parent element) | No
" | //schema-element(bu-core3d:Building)/bu-core3d:geometry2D/bu-base:BuildingGeometry2D/bu-base:verticalGeometryReference/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry2D/bu-base:BuildingGeometry2D/bu-base:verticalGeometryReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry2D/bu-base:BuildingGeometry2D/bu-base:verticalGeometryReference/@xlink:href | 0..1 (0..\* for the parent element) | No
verticalGeometryReference3DBottom <a name="verticalGeometryReference3DBottom"></a> | //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:verticalGeometryReference3DBottom <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:verticalGeometryReference3DBottom <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:verticalGeometryReference3DBottom <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:verticalGeometryReference3DBottom<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:verticalGeometryReference3DBottom | 0..1 | Yes
verticalGeometryReference3DTop <a name="verticalGeometryReference3DTop"></a> | //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:verticalGeometryReference3DTop<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:verticalGeometryReference3DTop<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:verticalGeometryReference3DTop | 0..1 | Yes
status <a name="status"></a> | //schema-element(bu-core2d:Building)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:status/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:status/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:status/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:status/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:status/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:heightAboveGround/bu-base:HeightAboveGround/bu-base:status/@xlink:href | 1 (0..\* for the parent element) | Yes
horizontalGeometryReference <a name="horizontalGeometryReference"></a> | //schema-element(bu-core2d:Building)/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:horizontalGeometryReference/@xlink:href | 1 | No
" | //schema-element(bu-core2d:BuildingPart)/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:horizontalGeometryReference/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:horizontalGeometryReference/@xlink:href | 1 (1..\* for the parent element) | No
" | //schema-element(bu-core3d:Building)/bu-core3d:geometry2D/bu-base:BuildingGeometry2D/bu-base:horizontalGeometryReference/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry2D/bu-base:BuildingGeometry2D/bu-base:horizontalGeometryReference/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry2D/bu-base:BuildingGeometry2D/bu-base:horizontalGeometryReference/@xlink:href | 1 (0..\* for the parent element) | No
" | //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:horizontalGeometryReference/@xlink:href | 0..1 | Yes
buildingNature <a name="buildingNature"></a> | //schema-element(bu-core2d:Building)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:buildingNature/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:buildingNature/@xlink:href | 0..\* | Yes
currentUse <a name="currentUse"></a> | //schema-element(bu-core2d:Building)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core2d:BuildingPart)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core3d:BuildingPart)/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-base:currentUse/bu-base:CurrentUse/bu-base:currentUse/@xlink:href | 1 (0..\* for the parent element) | No

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

* Check that all the [elevationReference](#elevationReference), [heightReference](#heightReference), [lowReference](#lowReference) and [verticalGeometryReference](#verticalGeometryReference) elements have a xlink:href attribute pointing to a [valid value](#validValue2). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).

* Check that all the [status](#status) elements has a xlink:href attribute pointing to a [valid value](#validValue3). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).

* Check that all the [horizontalGeometryReference](#horizontalGeometryReference) elements (if present) has a xlink:href attribute pointing to a [valid value](#validValue4). If the check fails report [disallowedCodeListValue](#disallowedCodeListValue).


| <a name="validValue1"></a> Valid values for xlink:href attribute of [conditionOfConstruction](#conditionOfConstruction) element are available in the INSPIRE Registry| 
| ---- | 
| ConditionOfConstructionValue: http://inspire.ec.europa.eu/codelist/ConditionOfConstructionValue | 

| <a name="validValue2"></a> Valid values for xlink:href attribute of [elevationReference](#elevationReference), [heightReference](#heightReference), [lowReference](#lowReference) and [verticalGeometryReference](#verticalGeometryReference) elements are available in the INSPIRE Registry.| 
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
TO BE COMPLETED
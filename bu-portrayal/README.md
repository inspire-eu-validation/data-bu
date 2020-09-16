# Conformance class: Portrayal, Buildings (DRAFT)

This conformance class is part of the [INSPIRE Data Specification on Buildings](../README.md).

## Standardization target type

View service

## Dependencies

### Direct dependencies

none

### Indirect dependencies

An indirect dependency is another conformance class whose requirements must be met by a related resource.

| Specification | Conformance class | Related resource | Parameters |
| ------------- | ----------------- | ---------------- | ---------- |
| [Technical Guidance for the implementation of INSPIRE View Services 3.11](#ref_TG_VS) | [Layer metadata](http://inspire.ec.europa.eu/id/ats/view-service/3.11/layer-metadata) | Capabilities document |  `service type`  |

## Parameters

A Conformance class may be parameterized, i.e. the class’s tests depend on some parameter that must be defined before the tests can be executed.
 
| Parameter | Values | Description |
| --------- | ------ | ----------- |
| `service type` | `ISO 19128` `WMTS 1.0.0` | The profile implemented by the view service | 

## External document references

| Abbreviation | Document name                       |
| ------------ | ----------------------------------- |
| TG DS-BU <a name="ref_TG_DS_BU"></a>   | [INSPIRE Data Specification on Buildings – Technical Guidelines version 3.0](http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_BU_v3.0.pdf)
| TG DS Template <a name="ref_TG_DS_tmpl"></a>   | [INSPIRE Data Specification Template version 3.0rc3](http://inspire.jrc.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_Template_v3.0rc3.pdf)
| TG VS <a name="ref_TG_VS"></a>   | [Technical Guidance for the implementation of INSPIRE View Services 3.11](http://inspire.jrc.ec.europa.eu/documents/Network_Services/TechnicalGuidance_ViewServices_v3.11.pdf)
| IR IOP <a name="ref_IR_IOP"><a/> | [COMMISSION REGULATION (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services](http://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L:2010:323:FULL&from=EN)
| IR IOP Amd 2 <a name="ref_IR_IOP_BUd2"><a/> | [COMMISSION REGULATION (EU) No 1253/2013 of 21 October 2013 amending Regulation (EU) No 1089/2010 implementing Directive 2007/2/EC as regards interoperability of spatial data sets and services](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2013:331:0001:0267:EN:PDF)

## Tests

This Conformance Class contains the following tests.

| Identifier                                                                          | Status   |
| ----------------------------------------------------------------------------------- | -------- |
| [Layers](./layers.md) | Ready for review |
| [Layer name](./layer-name.md) | Ready for review |

## Open issues

## XML namespace prefixes <a name="namespaces"></a>

The following prefixes are used to refer to the corresponding XML namespaces in all test descriptions:

Prefix         | Namespace
-------------- | -------------------------------------------------
wms            | http://www.opengis.net/wms
xlink          | http://www.w3.org/1999/xlink
gmd            | http://www.isotc211.org/2005/gmd
inspire_vs     | http://inspire.ec.europa.eu/schemas/inspire_vs/1.0
inspire_common | http://inspire.ec.europa.eu/schemas/common/1.0
wmts           | http://www.opengis.net/wmts/1.0
ows            | http://www.opengis.net/ows/1.1

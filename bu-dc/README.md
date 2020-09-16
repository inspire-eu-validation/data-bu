# Conformance class: Data consistency, Buildings

Conformance class for the requirements related to the consistency of the data.

To be able to test this conformance class, the encoding of the data set must be known, i.e. this is a parameterized conformance class. The XPath expressions used in this test suite assume that the GML encoding is used. If used with the GML encoding this conformance class has a direct dependency to the conformance class "INSPIRE GML application schemas".

This conformance class is part of the [INSPIRE Data Specification on Buildings](../README.md).

## Standardization target type

INSPIRE spatial data set

## Dependencies

### Direct dependencies

A direct dependency is another conformance class whose requirements must be met by the data set, too.

| Specification | Conformance class | Parameters | 
| ------------- | ----------------- | ---------- |
| [TG DS Template](#ref_TG_DS_tmpl) | [Data consistency](http://inspire.ec.europa.eu/id/ats/data/3.0rc3/data-consistency) | n/a |

### Indirect dependencies

none

 
## Feature types <a name="feature-types"></a>

The instantiable feature types are:

* Building
* BuildingPart

*Note*: The association between Building and BuildingPart is a composition, it implies a relationship where the child cannot exist independent of the parent. Building is the parent and BuildingPart is the child, so BuildingPart don't exist separate to a Building.
*Note*: When "features" or "spatial objects" are mentioned in the test cases, this refers only to instances of feature types of this application schema, not to any types specified in any other application schema.

## External document references

The following abbreviations are used in the test text for referring to external documents:

Abbreviation                     | Document name
-------------------------------- | --------------------------------------------------
TG DS-BU <a name="ref_TG_DS_BU"></a>   | [INSPIRE Data Specification on Buildings – Technical Guidelines version 3.0](http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_BU_v3.0.pdf)
TG DS Template <a name="ref_TG_DS_tmpl"></a>   | [INSPIRE Data Specification Template version 3.0rc3](http://inspire.jrc.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_Template_v3.0rc3.pdf)

## Test Cases

None, all data consistency test cases are covered by the generic [Data consistency](http://inspire.ec.europa.eu/id/ats/data/3.0rc3/data-consistency) tests.

## XML namespace prefixes <a name="namespaces"></a>

n/a

# Layers

**Purpose**: For the portrayal of spatial data sets using a view service, the layers for all spatial object types of the data theme specified in chapter 11 shall be available supporting the specified style(s).

**Prerequisites**

**Test method**

Inspect the view service, either through HTTP requests or using a software tool that is able to interact with the WMS/WMTS:
 
* Verify that all layers exist, for which the data set includes hydrographic features.
* Verify for each layer that title of the layer is the one specified in the column "Layer title" in sub-clamse 11.1 or one of the translations in section 8.8 in Annex II of the regulation ([IP IOP](./README.md#ref_IR_IOP), [IP IOP Amd 2](./README.md#ref_IR_IOP_BUd2)). 
* Using spot checks, verify for each layer that the rendered maps include the hydrographic objects in the data set.
* Verify for each layer and spatial object type included in the data set, that the default style specified in sub-clause 11.2 is implemented in the view service.

**Reference(s)**:

* [TG DS-BU](./README.md#ref_TG_DS_BU), IR Requirement, Article 14
* [TG DS-BU](./README.md#ref_TG_DS_BU), TG Requirement 7

**Test type**: Manual

**Notes**

## Contextual XPath references

n/a

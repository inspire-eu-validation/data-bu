# Layer name

**Purpose**: For the portrayal of spatial data sets using a view service, the layers specified in chapter 11 shall be available.

**Prerequisites**

**Test method**

* Check that at least one [layer name](#name) is one of the harmonized names for the data theme.

**Reference(s)**:

* [TG DS-BU](./README.md#ref_TG_DS_BU), IR Requirement, Article 14(1)(a)

**Test type**: Automated

**Notes**

## Contextual XPath references

The namespace prefixes used as described in [README.md](./README.md#namespaces).

Abbreviation                                     |  XPath expression												|  Parameter  value
------------------------------------------------ | ---------------------------------------------------------------	| ---------------------------------------------------------------
layer name <a name="name"></a> | /wms:WMS_Capabilities/wms:Capability/wms:Layer/wms:Name | ISO 19128

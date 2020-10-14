# Constraints

**Purpose**: Verify that the features provided in the dataset adhere to the constraints specified in the INSPIRE application schema.

**Prerequisites**

**Test method**

The following checks are performed for every feature in the dataset.

* **singleReferenceGeometry**: Check that exactly one geometry2D attribute is a reference geometry, i.e. a geometry2D with a [referenceGeometry](#referenceGeometry) attribute set to “true” (OCL: "inv: self.geometry2D->select(referenceGeometry=true)->size() = 1"). The check applies to both Building and BuildingPart feature types.

* **Building parts shall be 2D**: Check that the [parts](#parts) of the building is represented using the [BuildingPart](#BuildingPart) type of the Buildings2D package (OCL: "inv: self.parts->oclIsKindOf(Buildings2D::BuildingPart)"). If the representation is internal, throught a gml:id, the check is automated. If is external, using an url, the check is manual and the message will be 'manualReviewConstraintURL'.


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)
* [TG DS-BU](./README.md#ref_TG_DS_BU) 5.4.2.1.1., 5.4.2.1.2.

**Test type**: Automated + Manual check (if required)

**Notes** 

Verify that the OCL constraints that are specified in the UML model of the application schema are met, i.e. validate features against the constraints. For unmet constraints report [constraintViolation](#constraintViolation).

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
constraintViolation <a name="constraintViolation"/>  |  XML document '$filename', $featureType '$gmlid': The constraint '$constraint' is violated.
manualReviewConstraintURL <a name="manualReviewConstraintURL"/>  |  XML document '{filename}', {featureType} '{gmlid}': The property '{property}' has a value '{value}' that is referencing to a external association, please review that this external reference is represented using the BuildingPart type of the {type} package.

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression                     |Multiplicity       |Voidable
---------------------------------------------------------- | ------------------------------------- | ------------------|----------
referenceGeometry <a name="referenceGeometry"></a> | //schema-element(bu-core2d:Building)/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:referenceGeometry <br>  | 1 | No
" | //schema-element(bu-core2d:BuildingPart)/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:referenceGeometry <br>//schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart/bu-core2d:geometry2D/bu-base:BuildingGeometry2D/bu-base:referenceGeometry | 1 (1..\* for the parent element) | No
parts <a name="parts"></a> | //schema-element(bu-core2d:Building)/bu-base:parts | 0..\* | Yes
BuildingPart <a name="BuildingPart"></a> | //schema-element(bu-core2d:BuildingPart) <br> //schema-element(bu-core2d:Building)/bu-base:parts/bu-core2d:BuildingPart |  | 


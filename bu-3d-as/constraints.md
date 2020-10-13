# Constraints

**Purpose**: Verify that the features provided in the dataset adhere to the constraints specified in the INSPIRE application schema.

**Prerequisites**

**Test method**

The following checks are performed for every feature in the dataset.

* **GeometryWhenNoParts**: Check that if a Building does not have any BuildingParts, at least the [geometry3DLoD1](#g3DLoD1) or [geometry3DLoD2](#g3DLoD2) or [geometry3DLoD3](#g3DLoD3) or [geometry3DLoD4](#g3DLoD4) attributes is provided, for the Building feature type.

* **Building parts shall be 3D**: Check that the [parts](#parts) of the building is represented using the [BuildingPart](#BuildingPart) type of the Buildings3D package (OCL: "inv: self.parts->oclIsKindOf(Buildings3D::BuildingPart)"). If the representation is internal, throught a gml:id, the check is automated. If is external, using an url, the check is manual and the message will be 'manualReviewConstraintURL'.

* **MandatoryGeometry**: Check that at least one of the [geometry3DLoD1](#g3DLoD1_BP) or [geometry3DLoD2](#g3DLoD2_BP) or [geometry3DLoD3](#g3DLoD3_BP) or [geometry3DLoD4](#g3DLoD4_BP) attributes is provided, for the BuildingPart feature type.

* **oneGeometryToBeProvided**: Check that either the [geometryMultiSurface](#geometryMultiSurface) or the [geometrySolid](#geometrySolid) attribute is provided (OCL: "inv: self.geometryMultiSurface->notEmpty() or self.geometrySolid->notEmpty()")

* **no point referencing in 3D**: Check that the [horizontalGeometryReference](#horizontalGeometryReference) attribute does not take the value [entrancePoint](http://inspire.ec.europa.eu/codelist/HorizontalGeometryReferenceValue/entrancePoint), [pointInsideBuilding](http://inspire.ec.europa.eu/codelist/HorizontalGeometryReferenceValue/pointInsideBuilding) or [pointInsideCadastralParcel](http://inspire.ec.europa.eu/codelist/HorizontalGeometryReferenceValue/pointInsideCadastralParcel), in both BuildingGeometry3DLoD1 and BuildingGeometry3DLoD2 data types (OCL: "inv: self.horizontalGeometryReference->excludesAll(Set{HorizontalGeometryReferenceValue::entrancePoint, HorizontalGeometryReferenceValue::pointInsideBuilding , HorizontalGeometryReferenceValue::pointInsideCadastralParcel})"). 


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)
* [TG DS-BU](./README.md#ref_TG_DS_BU) 5.5.2.1.1., 5.5.2.1.2., 5.5.2.2.1., 5.5.2.2.2., 5.5.2.2.3.

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
geometry3DLoD1 (Building) <a name="g3DLoD1"></a> | //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD1  | 0..1 | No
geometry3DLoD2 (Building) <a name="g3DLoD2"></a> | //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD2  | 0..1 | No
geometry3DLoD3 (Building) <a name="g3DLoD3"></a> | //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD3  | 0..1 | No
geometry3DLoD4 (Building) <a name="g3DLoD4"></a> | //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD4  | 0..1 | No
parts <a name="parts"></a> | //schema-element(bu-core3d:Building)/bu-base:parts | 0..\* | Yes
BuildingPart <a name="BuildingPart"></a> | //schema-element(bu-core3d:BuildingPart) <br> //schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart |  | 
geometry3DLoD1 (BuildingPart) <a name="g3DLoD1_BP"></a> | //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD1 <br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD1 | 0..1 | No
geometry3DLoD2 (BuildingPart) <a name="g3DLoD2_BP"></a> | //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD2 <br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD2 | 0..1 | No
geometry3DLoD3 (BuildingPart) <a name="g3DLoD3_BP"></a> | //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD3 <br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD3 | 0..1 | No
geometry3DLoD4 (BuildingPart) <a name="g3DLoD4_BP"></a> | //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD4 <br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD4 | 0..1 | No
geometryMultiSurface <a name="geometryMultiSurface"></a> | //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:geometryMultiSurface <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:geometryMultiSurface <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometryMultiSurface <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometryMultiSurface<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometryMultiSurface | 0..1 | No
geometrySolid <a name="geometrySolid"></a> | //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:geometrySolid <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:geometrySolid <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD3/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometrySolid <br> //schema-element(bu-core3d:Building)bu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:BuildingPart)bu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometrySolid<br>//schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPartbu-core3d:geometry3DLoD4/bu-core3d:BuildingGeometry3DLoD/bu-core3d:geometrySolid | 0..1 | No
horizontalGeometryReference <a name="horizontalGeometryReference"></a> | //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:Building)/bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:BuildingPart)/bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD1/bu-core3d:BuildingGeometry3DLoD1/bu-core3d:horizontalGeometryReference/@xlink:href <br> //schema-element(bu-core3d:Building)/bu-base:parts/bu-core3d:BuildingPart/bu-core3d:geometry3DLoD2/bu-core3d:BuildingGeometry3DLoD2/bu-core3d:horizontalGeometryReference/@xlink:href | 0..1 | Yes

## Application Details
|               |
| ------------- |
|**Generation Date and Time**<br>Thu Apr 16 2026 16:47:46 GMT+0000 (Coordinated Universal Time)|
|**App Generator**<br>SAP Fiori Application Generator|
|**App Generator Version**<br>1.22.0|
|**Generation Platform**<br>SAP Business Application Studio|
|**Template Used**<br>List Report Page V2|
|**Service Type**<br>OData URL|
|**Service URL**<br>http://airdithanadev.airditsoftware.com:8010/sap/opu/odata/sap/ZP5_EMP_CDS|
|**Module Name**<br>p5felrcds|
|**Application Title**<br>List Report App with CDS|
|**Namespace**<br>com.demolscds|
|**UI5 Theme**<br>sap_horizon|
|**UI5 Version**<br>1.136.0|
|**Enable TypeScript**<br>False|
|**Add Eslint configuration**<br>True, see https://www.npmjs.com/package/@sap-ux/eslint-plugin-fiori-tools#rules for the eslint rules.|
|**Main Entity**<br>ZP5_EMP|
|**Navigation Entity**<br>to_prj|

## p5felrcds

An SAP Fiori application.

### Starting the generated app

-   This app has been generated using the SAP Fiori tools - App Generator, as part of the SAP Fiori tools suite.  To launch the generated application, run the following from the generated application root folder:

```
    npm start
```

- It is also possible to run the application using mock data that reflects the OData Service URL supplied during application generation.  In order to run the application with Mock Data, run the following from the generated app root folder:

```
    npm run start-mock
```

#### Pre-requisites:

1. Active NodeJS LTS (Long Term Support) version and associated supported NPM version.  (See https://nodejs.org)


## V12-13-14. Fiori Elements - List report with CDS and annotations

so we have Create three CDS views

### 1st ZP5_EMP

```html
<div style="max-height: 400px; overflow-y: auto; white-space: nowrap;">
<pre>
@AbapCatalog.sqlViewName: 'ZP5V_EMP'
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'Employee CDS for fiori element app'
@Metadata.ignorePropagatedAnnotations: true
@OData.publish: true

@UI.headerInfo:{typeName:'Employee',typeNamePlural:'Employees',title:{type:#STANDARD,value:'Empid'},
description:{type:#STANDARD,value:'Name'}}
@UI.lineItem: [{criticality: 'Statuscriticality'  }]

define view ZP5_EMP as select from zp5fe_employees
association [0..*] to ZP5_PRJ as _prj on $projection.Empid = _prj.Empid
{
@UI.facet: [{
    id:'idHFDesig',
    purpose:#HEADER,
    type:#DATAPOINT_REFERENCE,
    targetQualifier: 'Desig'
  },{
    id:'idHFSkill',
    purpose:#HEADER,
    type:#DATAPOINT_REFERENCE,
    targetQualifier: 'Skill'
  },{
    id:'idHFRating',
    purpose:#HEADER,
    type:#DATAPOINT_REFERENCE,
    targetQualifier: 'Rating'
  },{
    id:'idHFStatus',
    purpose:#HEADER,
    type:#DATAPOINT_REFERENCE,
    targetQualifier: 'Status'
  },{
  id:'idCFEmpInfo',
  label:'Employee Information',
  type:#COLLECTION,
  position:1
  },{
  id:'idBasicInfo',
  label:'Basic Info',
  type:#FIELDGROUP_REFERENCE,
  targetQualifier:'FGBasicInfo',
  parentId: 'idCFEmpInfo',
  position:1,
  purpose:#STANDARD
  },{
  id:'idSkillInfo',
  label:'Skill Info',
  type:#FIELDGROUP_REFERENCE,
  targetQualifier:'FGSkillInfo',
  parentId: 'idCFEmpInfo',
  position:2,
  purpose:#STANDARD
  },{
  id:'idPerfInfo',
  label:'Performance Info',
  type:#FIELDGROUP_REFERENCE,
  targetQualifier:'FGPerfInfo',
  parentId: 'idCFEmpInfo',
  position:3,
  purpose:#STANDARD
  }]

@UI.lineItem: [{position:1  }]
@UI.selectionField: [{position:1  }]
@Consumption.valueHelpDefinition: [{ entity:{name:'ZP5_VH_EMPID',element:'Empid' } }]
@EndUserText.label:'Employee ID'
@UI.fieldGroup: [{position:1,qualifier: 'FGBasicInfo'  }]
key empid as Empid,
@UI.lineItem: [{position:2  }]
@UI.fieldGroup: [{position:2,qualifier: 'FGBasicInfo'  }]
@EndUserText.label:'Name'
name as Name,
@UI.lineItem: [{position:3  }]
@UI.selectionField: [{position:2  }]
 @EndUserText.label:'Designation'
 @UI.dataPoint:{title: ' Designation'}
 @UI.fieldGroup: [{position:3,qualifier: 'FGBasicInfo'  }]
desig as Desig,
@UI.lineItem: [{position:4,importance:#LOW  }]
@UI.selectionField: [{position:3  }]
@Consumption.filter.defaultValue:'SAPUI5'
@UI.dataPoint:{title: 'Skill'}
@UI.fieldGroup: [{position:1,qualifier: 'FGSkillInfo'  }]
@EndUserText.label:'Skill'
skill as Skill,
@EndUserText.label:'Email'
@UI.fieldGroup: [{position:4,qualifier: 'FGBasicInfo'  }]
email as Email,
 @UI.lineItem: [{position:5,importance:#LOW  }]
 @UI.selectionField: [{position:4  }]
@UI.fieldGroup: [{position:1,qualifier: 'FGPerfInfo'  }]
@EndUserText.label:'Salary'
salary as Salary,

currencycode as Currencycode,
@UI.lineItem: [{position:6 ,criticality: 'Statuscriticality' }]
@UI.dataPoint:{title: 'Status',criticality :'Statuscriticality' }
@UI.fieldGroup: [{position:2,qualifier: 'FGPerfInfo'  }]
@EndUserText.label:'Status'
status as Status,
@UI.fieldGroup: [{position:3,qualifier: 'FGPerfInfo'  }]
@EndUserText.label:'Status Criticality'
statuscriticality as Statuscriticality,
@UI.lineItem: [{position:7 ,importance:#HIGH ,  type:#AS_DATAPOINT }]
@UI.dataPoint:{title:'Rating',visualization:#RATING ,targetValue: 5  }
@UI.fieldGroup: [{position:4,qualifier: 'FGPerfInfo'  }]
@EndUserText.label:'Rating'
rating as Rating,
@UI.lineItem: [{position:8 ,importance : #LOW  }]
 @EndUserText.label:'Date Of Joining'
 @UI.fieldGroup: [{position:5,qualifier: 'FGBasicInfo'  }]
doj as Doj ,
_prj
</pre>
</div>

### 2nd CDS View ZP5_PRJ

```html
<div style="max-height: 400px; overflow-y: auto; white-space: nowrap;">
<pre>
@AbapCatalog.sqlViewName: 'ZP5V_PRJ'
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'project cds'
@Metadata.ignorePropagatedAnnotations: true
define view ZP5_PRJ as select from zp5fe_projects
{
    key empid as Empid,
    key prjcode as Prjcode,
    clientname as Clientname,
    prjname as Prjname,
    prjdesc as Prjdesc,
    teamsize as Teamsize
}
</pre>
</div>

### 3rd EMP HELP   EMPID 

```html
<div style="max-height: 400px; overflow-y: auto; white-space: nowrap;">
<pre>
@AbapCatalog.sqlViewName: 'ZP5V_VH_EMPID'
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'view help cds view  fiori app'
@Metadata.ignorePropagatedAnnotations: true
@ObjectModel.resultSet.sizeCategory: #XS
define view ZP5_VH_EMPID as select from zp5fe_employees
{
    key empid as Empid,
    name as Name
}
</pre>
</div>


as of now v13 completed



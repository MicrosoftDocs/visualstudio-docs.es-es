---
title: "SharePoint Project Item Schema Reference"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Visual Studio usa el esquema de elementos de proyecto de SharePoint para validar el contenido de los archivos .spdata.  Un archivo .spdata especifica el contenido y el comportamiento de un elemento de proyecto de SharePoint.  Para obtener más información sobre el contenido de los elementos de proyecto de SharePoint, vea [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 El esquema de elementos de proyecto de SharePoint se denomina ProjectItemModelSchema.xsd y se instala de forma predeterminada en %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas.  
  
 El elemento raíz es el elemento [ProjectItem](../sharepoint/projectitem-element.md).  En la tabla siguiente se describen todos los elementos definidos por el esquema.  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Representa un elemento de datos personalizado que está asociado al elemento de proyecto de SharePoint y que tiene el formato clave\-valor.  La clave y el valor deben ser cadenas.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Representa una colección de valores de propiedad que se incluye con una característica cuando se implementa en SharePoint.  Una vez implementada la característica, se puede obtener acceso a los valores de propiedad en el código.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Representa una propiedad personalizada que se incluye con una característica cuando se implementa en SharePoint.  Una vez implementada la característica, se puede obtener acceso a la propiedad en el código.|  
|[Files \(Archivos\)](../sharepoint/files-element.md)|Especifica los archivos que se van a implementar con el elemento de proyecto de SharePoint, por ejemplo, un archivo de elemento de característica o la salida de un proyecto.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Representa un archivo de SharePoint, como un archivo de elemento de característica, que se va a incluir con el elemento de proyecto cuando se implemente en SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Representa una carpeta asignada.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Representa la salida de un proyecto que se va a incluir con el elemento de proyecto cuando se implemente en SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Representa un elemento web o control ASPX que se designa como seguro para que cualquier usuario pueda tener acceso a él en cualquier página ASPX del sitio de SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa una colección de elementos web y controles ASPX que se designan como seguros para que cualquier usuario pueda obtener acceso a ella en cualquier página ASPX del sitio de SharePoint.|  
  
## Vea también  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  
---
title: "ProjectOutputFile Element"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  Representa la salida de un proyecto independiente que se desea incluir con el elemento de proyecto cuando se implementa en SharePoint.  
  
## Sintaxis  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## Tipo  
 **ProjectOutputFileType**  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|**ProjectId**|El atributo **xs:string** es obligatorio.<br /><br /> El GUID del proyecto dependiente que tiene la salida que desea incluir.  Esto corresponde al elemento **ProjectGuid** en el archivo de proyecto dependiente.|  
|**ProjectPath**|El atributo **xs:string** es obligatorio.<br /><br /> La ruta de acceso relativa, incluido el nombre del archivo de proyecto, del proyecto dependiente que tiene la salida que desea incluir.  Esta ruta de acceso es relativa a la carpeta raíz del proyecto de SharePoint que contiene el elemento de proyecto de SharePoint.|  
|**Target**|Atributo **xs:string** opcional.<br /><br /> La ruta de acceso donde se implementará la salida del proyecto dependiente en el servidor de SharePoint, relativa a la carpeta raíz de implementación.  El tipo de implementación especificado por el atributo **Type** determina la carpeta raíz de implementación.<br /><br /> Para obtener más información, vea las descripciones de las propiedades **Deployment PathDeployment Root** de los elementos de proyecto de SharePoint en [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|El atributo **xs:string** es obligatorio.<br /><br /> El tipo de implementación que se desea utilizar para la salida del proyecto dependiente.  Para obtener más información sobre los valores posibles, vea la descripción de la propiedad **Deployment Type** de los elementos de proyecto de SharePoint en [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Files \(Archivos\)](../sharepoint/files-element.md)|Especifica los archivos que se desea incluir con el elemento de proyecto de SharePoint cuando se implementa en SharePoint.|  
  
## Comentarios  
 Utilice el elemento **ProjectOutputFile** para incluir la salida de un proyecto en la implementación del elemento de proyecto de SharePoint.  Puede especificar un proyecto diferente o el mismo proyecto que contiene el elemento de proyecto.  Para obtener más información, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## Vea también  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
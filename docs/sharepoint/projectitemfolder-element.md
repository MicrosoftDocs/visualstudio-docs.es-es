---
title: "ProjectItemFolder Element | Microsoft Docs"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  Representa una carpeta asignada.  
  
## Sintaxis  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## Tipo  
 **ProjectItemFolderType**  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|**Target**|El atributo **xs:string** es obligatorio.<br /><br /> La ruta de acceso de la carpeta de la instalación de SharePoint a la que corresponde la carpeta asignada, relativa a la carpeta raíz de implementación.  El tipo de implementación especificado por el atributo **Type** determina la carpeta raíz de implementación.<br /><br /> Para obtener más información, vea las descripciones de las propiedades **Deployment PathDeployment Root** de los elementos de proyecto de SharePoint en [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|El atributo **xs:string** es obligatorio.<br /><br /> El tipo de implementación para la carpeta asignada.  Para obtener más información sobre los valores posibles, vea la descripción de la propiedad **Deployment Type** de los elementos de proyecto de SharePoint en [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint.  Este es el elemento raíz necesario del archivo .spdata.|  
  
## Comentarios  
 Para obtener más información acerca de las carpetas asignadas, vea [Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## Vea también  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  
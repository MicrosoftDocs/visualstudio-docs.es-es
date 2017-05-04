---
title: "ProjectItemFile Element | Microsoft Docs"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  Representa un archivo de SharePoint, como un archivo de elemento de característica, que se va a incluir con el elemento de proyecto cuando se implemente en SharePoint.  
  
## Sintaxis  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## Tipo  
 **ProjectItemFileType**  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|**Source**|El atributo **xs:string** es obligatorio.<br /><br /> El nombre del archivo que se desea implementar con el elemento de proyecto.|  
|**Target**|Atributo **xs:string** opcional.<br /><br /> La ruta de acceso donde el archivo se implementará en SharePoint, relativa a la carpeta raíz de implementación.  El tipo de implementación especificado por el atributo **Type** determina la carpeta raíz de implementación.  Si no se especifica el atributo **Target**, el archivo se implementará en una carpeta con el nombre especificado en el atributo **Source**.<br /><br /> Para obtener más información, vea las descripciones de las propiedades **Deployment PathDeployment Root** de los elementos de proyecto de SharePoint en [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|El atributo **xs:string** es obligatorio.<br /><br /> El tipo de implementación para el archivo.  Para obtener más información sobre los valores posibles, vea la descripción de la propiedad **Deployment Type** de los elementos de proyecto de SharePoint en [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Files \(Archivos\)](../sharepoint/files-element.md)|Especifica los archivos que se desea incluir con el elemento de proyecto de SharePoint cuando se implementa en SharePoint.|  
  
## Comentarios  
 Los archivos de SharePoint a los que se hace referencia normalmente en los elementos **ProjectItemFile** incluyen archivos del elemento de Feature \(Elements.xml\), archivos de esquema para definiciones de lista \(Schema.xml\) y archivos de definición de Elemento web para Elementos web \(.webpart\).  
  
## Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## Vea también  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
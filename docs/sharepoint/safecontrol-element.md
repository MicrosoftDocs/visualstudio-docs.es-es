---
title: "SafeControl Element"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  Representa un elemento web o control ASPX que se designa como seguro para que cualquier usuario pueda tener acceso a él en cualquier página ASPX del sitio de SharePoint.  
  
## Sintaxis  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|**Assembly**|Atributo **xs:string** opcional.<br /><br /> El nombre del ensamblado en el que se define el control ASPX o elemento web.  De forma predeterminada, este atributo utiliza el parámetro reemplazable **$SharePoint.Project.AssemblyFullName$** para el nombre de ensamblado.  Para obtener más información, vea [Parámetros reemplazables](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Atributo **xs:boolean** opcional.<br /><br /> Especifica si el control ASPX o elemento web es seguro para que los usuarios que no son de confianza obtengan acceso.|  
|**IsSafeAgainstScript**|Atributo **xs:boolean** opcional.<br /><br /> Especifica si los usuarios que no son de confianza pueden ver o modificar las propiedades del control ASPX o elemento web.|  
|**Name**|Atributo **xs:string** opcional.<br /><br /> El nombre de esta entrada de control segura en la colección.|  
|**Namespace**|Atributo **xs:string** opcional.<br /><br /> El espacio de nombres del control ASPX o elemento web.|  
|**TypeName**|Atributo **xs:string** opcional.<br /><br /> El nombre de tipo del control ASPX o elemento web.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Representa una colección de elementos web y controles ASPX que se designan como seguros para que cualquier usuario pueda obtener acceso a ella en cualquier página ASPX del sitio de SharePoint.|  
  
## Comentarios  
 Para obtener más información acerca de los controles seguros, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  
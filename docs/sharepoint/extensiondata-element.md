---
title: "ExtensionData Element"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.  
  
## Sintaxis  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento opcional.<br /><br /> Representa un elemento de datos personalizado que está asociado al elemento de proyecto de SharePoint y que tiene el formato clave\-valor.  La clave y el valor deben ser cadenas.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint.  Este es el elemento raíz necesario del archivo .spdata.|  
  
## Comentarios  
 Al asociar datos personalizados a un elemento de proyecto de SharePoint utilizando la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, Visual Studio guarda los datos en un nuevo elemento **ExtensionData** en el archivo .spdata del elemento de proyecto.  Para obtener más información, vea [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## Vea también  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
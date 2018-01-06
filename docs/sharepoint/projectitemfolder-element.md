---
title: ProjectItemFolder (elemento) | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: ProjectItemFolder element
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c6b5c895f36f3e0b040ce1e3db7cb87cd52e5b9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder (Elemento)
  Representa una carpeta asignada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**Target**|Requiere **xs: String** atributo.<br /><br /> La ruta de acceso de la carpeta en la instalación de SharePoint que corresponde la carpeta asignada, relativa a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el **tipo** atributo.<br /><br /> Para obtener más información, vea las descripciones de los **ruta de acceso de implementación** y **raíz de la implementación** propiedades de SharePoint elementos de proyecto en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requiere **xs: String** atributo.<br /><br /> El tipo de implementación para la carpeta asignada. Para obtener más información acerca de los valores posibles, vea la descripción de la **tipo de implementación** propiedad de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este es el elemento raíz necesario del archivo .spdata.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las carpetas asignadas, vea [Cómo: agregar y quitar carpetas asignado](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  
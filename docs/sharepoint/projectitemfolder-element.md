---
title: ProjectItemFolder (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54d47165117b88041346e9b666db8db17a20ddb9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119923"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder (elemento)
  Representa una carpeta asignada.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
|**Target**|Requiere **xs: string** atributo.<br /><br /> La ruta de acceso de la carpeta en la instalación de SharePoint que corresponde la carpeta asignada, relativa a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el **tipo** atributo.<br /><br /> Para obtener más información, vea las descripciones de los **Deployment Path** y **Deployment Root** propiedades de SharePoint elementos de proyecto en [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requiere **xs: String** atributo.<br /><br /> El tipo de implementación para la carpeta asignada. Para obtener más información acerca de los valores posibles, vea la descripción para el **tipo de implementación** propiedad de los elementos de proyecto de SharePoint en [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos secundarios
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento es el elemento raíz necesario de la *.spdata* archivo.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las carpetas asignadas, consulte [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Información de elemento
  
|||  
|-|-|  
|**Espacio de nombres**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también
 [Referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  

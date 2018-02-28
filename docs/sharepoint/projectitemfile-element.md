---
title: ProjectItemFile (elemento) | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 7c222c25417f9a33f28871c94d8dd0d9353e1e76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="projectitemfile-element"></a>ProjectItemFile (Elemento)
  Representa un archivo de SharePoint, como archivo de elemento de característica, se incluyen con el elemento de proyecto cuando se implementa en SharePoint.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**Origen**|Requiere **xs: String** atributo.<br /><br /> El nombre de archivo que se va a implementar con el elemento de proyecto.|  
|**Target**|Opcional **xs: String** atributo.<br /><br /> La ruta de acceso donde se implementará el archivo en SharePoint, relativa a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el **tipo** atributo. Si el **destino** atributo no se especifica, el archivo se implementará en una carpeta con el nombre especificado en el **origen** atributo.<br /><br /> Para obtener más información, vea las descripciones de los **ruta de acceso de implementación** y **raíz de la implementación** propiedades de SharePoint elementos de proyecto en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requiere **xs: String** atributo.<br /><br /> El tipo de implementación para el archivo. Para obtener más información acerca de los valores posibles, vea la descripción de la **tipo de implementación** propiedad de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos que desea incluir con el elemento de proyecto de SharePoint cuando se implementa en SharePoint.|  
  
## <a name="remarks"></a>Comentarios  
 Archivos de SharePoint que normalmente se hace referencia en **ProjectItemFile** elementos incluyen archivos del elemento Feature (Elements.xml), archivos de esquema para las definiciones de lista (Schema.xml) y archivos de definición de elemento Web de elementos Web (.webpart).  
  
## <a name="element-information"></a>Información de elemento  
  
|||  
|-|-|  
|**Espacio de nombres**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de los elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
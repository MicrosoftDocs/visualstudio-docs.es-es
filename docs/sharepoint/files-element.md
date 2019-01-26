---
title: Archivos elemento | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b25bb220d3c22af280a486de115193af38c85dbe
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864532"
---
# <a name="files-element"></a>Files (elemento)
  Especifica los archivos para implementar con el elemento de proyecto de SharePoint, como los archivos de elemento de característica y la salida de los proyectos de SharePoint que no son dependientes.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>Tipo  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Opcional **ProjectItemFileType** elemento.<br /><br /> Representa un archivo de SharePoint, como archivo de elemento de característica, se incluyen con el elemento de proyecto cuando se implementa en SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Opcional **ProjectOutputFileType** elemento.<br /><br /> Representa la salida de un proyecto para incluir con el elemento de proyecto cuando se implementa en SharePoint.|  
  
### <a name="parent-elements"></a>Elementos primarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento, el elemento raíz necesario de la `.spdata` archivo.|  
  
## <a name="element-information"></a>Información de elemento
  
|||  
|-|-|  
|**Espacio de nombres**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también
 [Referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  

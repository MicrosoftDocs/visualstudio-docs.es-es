---
title: ExtensionData (elemento) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c50eac5a470a2800acff89316bd53fda683d6b0f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922167"
---
# <a name="extensiondata-element"></a>ExtensionData (elemento)
  Representa una colección de elementos de datos personalizados que están asociados con el elemento de proyecto de SharePoint.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento opcional.<br /><br /> Representa un elemento de datos personalizado que está asociado con el elemento de proyecto de SharePoint, en formato de clave/valor. La clave y el valor deben ser cadenas.|  
  
### <a name="parent-elements"></a>Elementos primarios
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento, el elemento raíz necesario de la `.spdata` archivo.|  
  
## <a name="remarks"></a>Comentarios  
 Al asociar datos personalizados a un elemento de proyecto de SharePoint con el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto, Visual Studio guarda los datos a la **ExtensionData** elemento en el `.spdata` archivo del proyecto elemento. Para obtener más información, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Información de elemento
  
|||  
|-|-|  
|**Espacio de nombres**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel/SharePointTools/2010|  
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también
 [Referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  

---
title: ExtensionDataItem (elemento) | Documentos de Microsoft
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
helpviewer_keywords: ExtensionDataItem element
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 57e6d01e918256217e94077f6414651e50dd4c74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem (Elemento)
  Representa un elemento de datos personalizado que está asociado con el elemento de proyecto de SharePoint, en formato de clave/valor. La clave y el valor deben ser cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**Key**|Requiere **xs: String** atributo.<br /><br /> La clave que se utiliza para almacenar y recuperar el elemento de datos.|  
|**Valor**|Requiere **xs: String** atributo.<br /><br /> El valor del elemento de datos.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa una colección de elementos de datos personalizados que están asociados con el elemento de proyecto de SharePoint.|  
  
## <a name="remarks"></a>Comentarios  
 Al asociar datos personalizados con un elemento de proyecto de SharePoint utilizando la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto, Visual Studio guarda los datos en una nueva **ExtensionDataItem** elemento en el archivo .spdata del elemento de proyecto. Para obtener más información, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Información de elemento  
  
|||  
|-|-|  
|**Namespace**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|  
|**Archivo de validación**|ProjectItemModelSchema.xsd|  
|**Puede estar vacío**|No|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de los elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
---
title: Elemento Extensiondata (| Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b700239f97153cef94ab1d7010ad16ed9aa6001
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546567"
---
# <a name="extensiondata-element"></a>ExtensionData (elemento)
  Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.

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
|[Extensiondataitem (](../sharepoint/extensiondataitem-element.md)|Elemento opcional.<br /><br /> Representa un elemento de datos personalizado que está asociado al elemento de proyecto de SharePoint, en formato de clave y valor. La clave y el valor deben ser cadenas.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento es el elemento raíz necesario del `.spdata` archivo.|

## <a name="remarks"></a>Comentarios
 Al asociar datos personalizados a un elemento de proyecto de SharePoint mediante la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto, Visual Studio guarda los datos en el elemento **extensiondata (** en el `.spdata` archivo para el elemento de proyecto. Para obtener más información, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Vea también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)

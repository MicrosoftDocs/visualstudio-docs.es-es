---
title: Elemento Extensiondataitem (| Microsoft Docs
description: Vea la información de referencia sobre el elemento Extensiondataitem (, que es un elemento del esquema del elemento de proyecto de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: add1a119283635f9cfd9bebddfe18228f1976703
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876828"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem (elemento)
  Un elemento de datos personalizado que está asociado al elemento de proyecto de SharePoint, en formato de clave/valor. La clave y el valor deben ser cadenas.

## <a name="syntax"></a>Sintaxis

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|**Clave**|Atributo **xs: String** requerido.<br /><br /> Clave que se usa para almacenar y recuperar el elemento de datos.|
|**Valor**|Atributo **xs: String** requerido.<br /><br /> Valor del elemento de datos.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa una colección de elementos de datos personalizados que están asociados al elemento de proyecto de SharePoint.|

## <a name="remarks"></a>Notas
 Al asociar datos personalizados a un elemento de proyecto de SharePoint mediante la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto, Visual Studio guarda los datos en un nuevo elemento **extensiondataitem (** en el `.spdata` archivo para el elemento de proyecto. Para obtener más información, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Consulte también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)

---
title: Elemento Projectitemfolder (| Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539820"
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
|**Target**|Atributo **xs: String** requerido.<br /><br /> La ruta de acceso de la carpeta en la instalación de SharePoint a la que corresponde la carpeta asignada, relativa a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el atributo **Type** .<br /><br /> Para obtener más información, vea las descripciones de las propiedades **ruta de implementación** y **raíz de implementación** de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Atributo **xs: String** requerido.<br /><br /> El tipo de implementación para la carpeta asignada. Para obtener más información sobre los valores posibles, vea la descripción de la propiedad **tipo de implementación** de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento es el elemento raíz necesario del archivo *. spdata* .|

## <a name="remarks"></a>Comentarios
 Para obtener más información acerca de las carpetas asignadas, consulte [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Vea también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)

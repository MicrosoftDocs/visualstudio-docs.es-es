---
title: ProjectItemFile (elemento) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57c491c79030eea1a01024235c01aec425d5994c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562368"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (elemento)
  Representa un archivo de SharePoint, como archivo de elemento de característica, se incluyen con el elemento de proyecto cuando se implementa en SharePoint.

## <a name="syntax"></a>Sintaxis

```xml
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
|**Origen**|Requiere **xs: String** atributo.<br /><br /> El nombre del archivo que se va a implementar con el elemento de proyecto.|
|**Target**|Opcional **xs: String** atributo.<br /><br /> La ruta de acceso donde se implementará el archivo en SharePoint, relativa a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el **tipo** atributo. Si el **destino** atributo no se especifica, el archivo se implementará en una carpeta con el nombre especificado en el **origen** atributo.<br /><br /> Para obtener más información, vea las descripciones de los **Deployment Path** y **Deployment Root** propiedades de SharePoint elementos de proyecto en [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Requiere **xs: String** atributo.<br /><br /> El tipo de implementación para el archivo. Para obtener más información acerca de los valores posibles, vea la descripción para el **tipo de implementación** propiedad de los elementos de proyecto de SharePoint en [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos que se incluirá con el elemento de proyecto de SharePoint cuando se implementa en SharePoint.|

## <a name="remarks"></a>Comentarios
 Los archivos de SharePoint que se suele hacer referencia a **ProjectItemFile** elementos incluyen archivos de elemento de característica (*Elements.xml*), archivos de esquema para definiciones de lista (*Schema.xml*) y los archivos de definición de elemento Web para elementos Web (*.webpart*).

## <a name="element-information"></a>Información de elemento

|||
|-|-|
|**Espacio de nombres**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre de esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema.xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Vea también
- [Referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)

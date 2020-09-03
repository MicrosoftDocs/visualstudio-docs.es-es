---
title: Elemento Projectitemfile (| Microsoft Docs
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
ms.openlocfilehash: d1c9814498d74a5d1a6533576f1071b4bf7deb57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539859"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (elemento)
  Representa un archivo de SharePoint, como el archivo de elemento de característica, que se va a incluir con el elemento de proyecto cuando se implemente en SharePoint.

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
|**Origen**|Atributo **xs: String** requerido.<br /><br /> Nombre del archivo que se va a implementar con el elemento de proyecto.|
|**Destino**|Atributo **xs: String** opcional.<br /><br /> La ruta de acceso donde se implementará el archivo en SharePoint, con respecto a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el atributo **Type** . Si no se especifica el atributo de **destino** , el archivo se implementará en una carpeta con el nombre especificado en el atributo de **origen** .<br /><br /> Para obtener más información, vea las descripciones de las propiedades **ruta de implementación** y **raíz de implementación** de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Atributo **xs: String** requerido.<br /><br /> El tipo de implementación para el archivo. Para obtener más información sobre los valores posibles, vea la descripción de la propiedad **tipo de implementación** de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos que se incluirán con el elemento de proyecto de SharePoint cuando se implemente en SharePoint.|

## <a name="remarks"></a>Observaciones
 Los archivos de SharePoint a los que se hace referencia normalmente en elementos **projectitemfile (** incluyen archivos de elementos de características (*Elements.xml*), archivos de esquema para definiciones de lista (*Schema.xml*) y archivos de definición de elementos Web para elementos Web (*. WebPart*).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Consulte también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)

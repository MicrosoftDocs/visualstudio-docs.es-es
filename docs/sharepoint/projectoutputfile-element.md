---
title: Elemento ProjectOutputFile (| Microsoft Docs
description: Obtiene información de referencia sobre el elemento ProjectOutputFile (, que representa la salida de un proyecto independiente en la referencia de esquema XML del elemento de proyecto de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a3b5a0f6474231fdc8f7617040ec4aa57056d9c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966960"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile (elemento)
  Representa la salida de un proyecto independiente que se incluirá con el elemento de proyecto cuando se implemente en SharePoint.

## <a name="syntax"></a>Sintaxis

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Tipo
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|**ProjectId**|Atributo **xs: String** requerido.<br /><br /> GUID del proyecto dependiente que tiene el resultado que desea incluir. Esto corresponde al elemento **ProjectGuid** del archivo de proyecto dependiente.|
|**ProjectPath**|Atributo **xs: String** requerido.<br /><br /> La ruta de acceso relativa, incluido el nombre de archivo del proyecto dependiente, que tiene el resultado que desea incluir. Esta ruta de acceso es relativa a la carpeta raíz del proyecto de SharePoint que contiene el elemento de proyecto de SharePoint.|
|**Target**|Atributo **xs: String** opcional.<br /><br /> La ruta de acceso donde se implementará el resultado del proyecto dependiente en el servidor de SharePoint, con respecto a la carpeta raíz de implementación. La carpeta raíz de implementación viene determinada por el tipo de implementación especificado por el atributo **Type** .<br /><br /> Para obtener más información, vea las descripciones de las propiedades **ruta de implementación** y **raíz de implementación** de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Atributo **xs: String** requerido.<br /><br /> Tipo de implementación que se va a usar para la salida del proyecto dependiente. Para obtener más información sobre los valores posibles, vea la descripción de la propiedad **tipo de implementación** de los elementos de proyecto de SharePoint en [desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Archivos](../sharepoint/files-element.md)|Especifica los archivos que se incluirán con el elemento de proyecto de SharePoint cuando se implemente en SharePoint.|

## <a name="remarks"></a>Notas
 Use el elemento **ProjectOutputFile (** para incluir la salida de un proyecto en la implementación del elemento de proyecto de SharePoint. Puede especificar un proyecto diferente o el mismo proyecto que contiene el elemento de proyecto. Para obtener más información, vea [proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Consulte también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Inclusión de información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)

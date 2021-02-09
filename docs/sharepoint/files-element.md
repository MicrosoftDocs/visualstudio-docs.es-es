---
title: Elemento files | Microsoft Docs
description: Vea la información de referencia sobre el elemento files, que es un elemento del esquema del elemento de proyecto de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 653e48a2e9b6a68db94fd66660da85f4dec20927
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876652"
---
# <a name="files-element"></a>Files (elemento)
  Especifica los archivos que se van a implementar con el elemento de proyecto de SharePoint, como los archivos de elemento de característica y la salida de proyectos dependientes que no son de SharePoint.

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
|[Projectitemfile (](../sharepoint/projectitemfile-element.md)|Elemento **ProjectItemFileType** opcional.<br /><br /> Representa un archivo de SharePoint, como el archivo de elemento de característica, que se va a incluir con el elemento de proyecto cuando se implemente en SharePoint.|
|[ProjectOutputFile (](../sharepoint/projectoutputfile-element.md)|Elemento **ProjectOutputFileType** opcional.<br /><br /> Representa la salida de un proyecto que se incluirá con el elemento de proyecto cuando se implemente en SharePoint.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa un elemento de proyecto de SharePoint. Este elemento es el elemento raíz necesario del `.spdata` archivo.|

## <a name="element-information"></a>Información de elemento

|Propiedad|Value|
|-|-|
|**Espacio de nombres**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nombre del esquema**|Esquema de elemento de proyecto de SharePoint|
|**Archivo de validación**|ProjectItemModelSchema. xsd|
|**Puede estar vacío**|No|

## <a name="see-also"></a>Consulte también
- [Referencia de esquemas de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)

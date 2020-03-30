---
title: La estructura del archivo [Content_types].xml Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957958cd930620734d09c592ea07bfb0919d0145
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395315"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Estructura del archivo [Content_types].xml
Contiene información sobre los tipos de contenido de un paquete VSIX. Visual Studio usa el archivo [Content_Types].xml para instalar el paquete, pero no instala el archivo en sí.

> [!NOTE]
> Aunque este tema solo se aplica a los archivos [Content_Type].xml que se usan en paquetes VSIX, el tipo de archivo [Content_Types].xml forma parte del estándar *Open Packaging Conventions (OPC).* Para obtener más información, consulte [OPC: un nuevo estándar para empaquetar](https://msdn.microsoft.com/magazine/cc163372.aspx) los datos en el sitio Web de MSDN.

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las secciones siguientes se describe el elemento raíz y sus atributos y elementos secundarios.

### <a name="root-element"></a>Elemento raíz

|Elemento|Descripción|
|-------------|-----------------|
|`Types`|Contiene elementos secundarios que enumeran los tipos de archivo en el paquete VSIX.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Xmlns`|(Requerido.) La ubicación del esquema utilizado para este archivo [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>•Nombre del atributo ? Atributo

| Valor | Descripción |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | La ubicación del esquema de tipos de contenido. |

### <a name="child-elements"></a>Elementos secundarios
 El elemento `Types` puede contener cualquier número de elementos `Default`.

|Elemento|Descripción|
|-------------|-----------------|
|`Default`|Describe un tipo de contenido en el paquete VSIX. Cada tipo de archivo del `Default` paquete debe tener su propio elemento.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Extension`|La extensión de nombre de archivo de un archivo en el paquete VSIX.|
|`ContentType`|Describe el tipo de contenido asociado a la extensión de nombre de archivo.|

### <a name="attribute-name-attribute"></a>•Nombre del atributo ? Atributo
 Visual Studio reconoce `ContentType` los siguientes `Extension` valores para los tipos asociados.

|Extensión|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm o html|text/html|
|Rtf|aplicación/rtf|
|pdf|aplicación/pdf|
|GIF|image/gif|
|jpg o jpeg|imagen/jpg|
|tiff|image/tiff|
|vsix|aplicación/zip|
|zip|aplicación/zip|
|dll|application/octet-stream|
|todos los demás tipos de archivos|application/octet-stream|

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción
 El siguiente archivo [Content_Types].xml describe un paquete VSIX típico.

### <a name="code"></a>Código

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Vea también
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Referencia del esquema de extensión 1.0 de VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: Un nuevo estándar para empaquetar sus datos](https://msdn.microsoft.com/magazine/cc163372.aspx)
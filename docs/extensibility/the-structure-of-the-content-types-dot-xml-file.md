---
title: Estructura del archivo de .xml [Content_types]| Microsoft Docs
description: Obtenga información sobre la estructura del archivo de tipos de contenido, que contiene información sobre los tipos de contenido de un paquete VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96d4d0eeea34300894674a2105d080e8a6abb607
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900426"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Estructura del archivo [Content_types].xml
Contiene información sobre los tipos de contenido de un paquete VSIX. Visual Studio usa el archivo [Content_Types].xml para instalar el paquete, pero no instala el propio archivo.

> [!NOTE]
> Aunque este tema solo se aplica a los archivos [Content_Type].xml que se usan en paquetes VSIX, el tipo de archivo [Content_Types].xml forma parte del estándar *Convenciones de empaquetado abierto (OPC).* Para obtener más información, [vea OPC: A New Standard For Packaging Your Data (OPC: un nuevo estándar para empaquetar los](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) datos) en el sitio web de MSDN.

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las secciones siguientes se describe el elemento raíz y sus atributos y elementos secundarios.

### <a name="root-element"></a>Elemento raíz

|Elemento|Descripción|
|-------------|-----------------|
|`Types`|Contiene elementos secundarios que enumeran los tipos de archivo en el paquete VSIX.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Xmlns`|(Obligatorio). Ubicación del esquema utilizado para este archivo [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo

| Valor | Descripción |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Ubicación del esquema de tipos de contenido. |

### <a name="child-elements"></a>Elementos secundarios
 El elemento `Types` puede contener cualquier número de elementos `Default`.

|Elemento|Descripción|
|-------------|-----------------|
|`Default`|Describe un tipo de contenido en el paquete VSIX. Cada tipo de archivo del paquete debe tener su propio `Default` elemento.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Extension`|Extensión de nombre de archivo de un archivo en el paquete VSIX.|
|`ContentType`|Describe el tipo de contenido asociado a la extensión de nombre de archivo.|

### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo
 Visual Studio reconoce los siguientes `ContentType` valores para los tipos `Extension` asociados.

|Extensión|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm o html|text/html|
|Rtf|application/rtf|
|pdf|application/pdf|
|GIF|image/gif|
|jpg o jpeg|image/jpg|
|tiff|image/tiff|
|vsix|application/zip|
|zip|application/zip|
|dll|application/octet-stream|
|todos los demás tipos de archivo|application/octet-stream|

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción
 El siguiente archivo de Content_Types].xml describe un paquete VSIX típico.

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

## <a name="see-also"></a>Consulte también
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Referencia del esquema de extensión VSIX 1.0](/previous-versions/dd393700(v=vs.110))
- [OPC: un nuevo estándar para empaquetar los datos](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)
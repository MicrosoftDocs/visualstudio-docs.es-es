---
title: Estructura del archivo [Content_types]. XML | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e96af4936f27d869409a7215c720d9bb64e4128
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012522"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Estructura del archivo [Content_types].xml
Contiene información sobre los tipos de contenido de un paquete VSIX. Visual Studio usa el archivo [Content_Types]. XML para instalar el paquete, pero no instala el propio archivo.

> [!NOTE]
> Aunque este tema se aplica únicamente a los archivos [Content_Type]. XML que se usan en los paquetes VSIX, el tipo de archivo [Content_Types]. XML forma parte del estándar de *convenciones de empaquetado abierto (OPC)* . Para obtener más información, consulte [OPC: un nuevo estándar para empaquetar los datos](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) en el sitio web de MSDN.

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las secciones siguientes se describe el elemento raíz y sus atributos y elementos secundarios.

### <a name="root-element"></a>Elemento raíz

|Elemento|Descripción|
|-------------|-----------------|
|`Types`|Contiene elementos secundarios que enumeran los tipos de archivo del paquete VSIX.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Xmlns`|(Obligatorio). La ubicación del esquema utilizado para este archivo [Content_Types]. Xml.|

### <a name="attribute-name-attribute"></a>{Nombre de atributo} Atribui

| Value | Descripción |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | La ubicación del esquema de tipos de contenido. |

### <a name="child-elements"></a>Elementos secundarios
 El elemento `Types` puede contener cualquier número de elementos `Default`.

|Elemento|Descripción|
|-------------|-----------------|
|`Default`|Describe un tipo de contenido en el paquete VSIX. Todos los tipos de archivo del paquete deben tener su propio `Default` elemento.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Extension`|La extensión de nombre de archivo de un archivo en el paquete VSIX.|
|`ContentType`|Describe el tipo de contenido asociado a la extensión de nombre de archivo.|

### <a name="attribute-name-attribute"></a>{Nombre de atributo} Atribui
 Visual Studio reconoce los siguientes `ContentType` valores para los `Extension` tipos asociados.

|Extensión|ContentType|
|---------------|-----------------|
|txt|text/plain|
|archivo pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm o HTML|text/html|
|RTF|aplicación/RTF|
|pdf|aplicación/pdf|
|GIF|image/gif|
|jpg o JPEG|imagen/jpg|
|tiff|image/tiff|
|vsix|aplicación/código postal|
|zip|aplicación/código postal|
|dll|application/octet-stream|
|todos los demás tipos de archivo|application/octet-stream|

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción
 El siguiente archivo [Content_Types]. XML describe un paquete VSIX típico.

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
- [Referencia del esquema de extensión VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [OPC: un nuevo estándar para empaquetar los datos](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)
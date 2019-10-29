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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac250053f90d99e7db27a9862d2dc1b33fadbfb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983038"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Estructura del archivo [Content_types].xml
Contiene información sobre los tipos de contenido de un paquete VSIX. Visual Studio usa el archivo [Content_Types]. XML para instalar el paquete, pero no instala el propio archivo.

> [!NOTE]
> Aunque este tema se aplica solo a los archivos [Content_Type]. XML que se usan en los paquetes VSIX, el tipo de archivo [Content_Types]. XML forma parte del estándar de *convenciones de empaquetado abierto (OPC)* . Para obtener más información, consulte [OPC: un nuevo estándar para empaquetar los datos](https://msdn.microsoft.com/magazine/cc163372.aspx) en el sitio web de MSDN.

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las secciones siguientes se describe el elemento raíz y sus atributos y elementos secundarios.

### <a name="root-element"></a>Elemento raíz

|Elemento|Descripción|
|-------------|-----------------|
|`Types`|Contiene elementos secundarios que enumeran los tipos de archivo del paquete VSIX.|

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Xmlns`|(Obligatorio). La ubicación del esquema que se usa para este archivo [Content_Types]. Xml.|

### <a name="attribute-name-attribute"></a>{Nombre de atributo} Atribui

| Valor | Descripción |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | La ubicación del esquema de tipos de contenido. |

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
 Visual Studio reconoce los siguientes valores de `ContentType` para los tipos de `Extension` asociados.

|Comprobación de actualización|ContentType|
|---------------|-----------------|
|txt|texto/sin formato|
|archivo pkgdef|texto/sin formato|
|xml|text/xml|
|vsixmanifest|text/xml|
|htm o HTML|texto/HTML|
|RTF|aplicación/RTF|
|archivo|aplicación/pdf|
|GIF|imagen/GIF|
|jpg o JPEG|imagen/jpg|
|TIFF|imagen/TIFF|
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

## <a name="see-also"></a>Vea también
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Referencia del esquema de extensión VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: un nuevo estándar para empaquetar los datos](https://msdn.microsoft.com/magazine/cc163372.aspx)
---
title: Referencia del esquema del paquete de idioma VSIX 2,0 | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: zorio
author: zoeyr
manager: jillfra
ms.openlocfilehash: fe6d4bd9e82950d77925dda1560b5c204633d392
ms.sourcegitcommit: dae5dfd626277b58ebd7b21a75757f683f1eacc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739330"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Referencia del esquema del paquete de idioma VSIX 2,0

El esquema del paquete de idioma VSIX proporciona información de instalación localizada para los paquetes VSIX. La versión 2,0 de este esquema admite elementos de localización adicionales.

## <a name="language-pack-schema"></a>Esquema del paquete de idioma

El elemento raíz del archivo de paquete de idioma `<PackageLanguagePackManifest>`es, con un atributo `Version`de, que es la versión del formato del paquete de idioma. En este artículo se describe la versión 2,0 del formato de paquete de idioma, que se especifica en el `Version` manifiesto estableciendo el atributo `Version="2.0.0"`en el valor. El elemento raíz contiene exactamente un elemento `<Metadata>` secundario.

### <a name="packagelanguagepackmanifest-element"></a>Elemento PackageLanguagePackManifest

Dentro del `<PackageLanguagePackManifest>` elemento debe existir el siguiente elemento:

|Título|DESCRIPCIÓN|
|-----------|-----------------|
|`<Metadata>`| El elemento contenedor para todos los metadatos de paquete localizados

### <a name="metadata-element"></a>Elemento metadata

Dentro del `<Metadata>` elemento puede tener los elementos siguientes:

|Título|DESCRIPCIÓN|
|-----------|-----------------|
|`<DisplayName>`|Nombre localizado de la extensión que se va a instalar.|
|`<Description>`|La descripción localizada de la extensión que se va a instalar.|
|`<License>`| Una ruta de acceso a una versión localizada de la licencia de la extensión|
|`<MoreInfo>`| Un vínculo a información localizada sobre la extensión|
|`<ReleaseNotes>`| Una ruta de acceso o un vínculo a una versión localizada de las notas de la versión|
|`<Icon>`| Una ruta de acceso a una versión localizada del icono de extensiones|

### <a name="sample-manifest"></a>Manifiesto de ejemplo

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Vea también

|Título|DESCRIPCIÓN|
|-----------|-----------------|
|[Localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Muestra cómo proporcionar compatibilidad con la instalación localizada para un paquete VSIX.|
|[Referencia del esquema de extensión VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifiesto VSIX describe el contenido de un archivo de implementación *. vsix* . El archivo de implementación permite instalar una extensión de Visual Studio mediante el cuadro de diálogo **extensiones y actualizaciones** .|
|[Búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Muestra cómo usar el cuadro de diálogo **extensiones y actualizaciones** para instalar, quitar, activar y desactivar extensiones.|

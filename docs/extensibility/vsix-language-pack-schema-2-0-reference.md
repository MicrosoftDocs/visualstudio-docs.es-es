---
title: Referencia de esquema 2.0 del paquete de idioma VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 73429f0ec41285dbab995a8a09411e5197bd0892
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889181"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Referencia de esquema 2.0 del paquete de idioma VSIX

El esquema del paquete de idioma de VSIX proporciona información de instalación localizada para paquetes VSIX. La versión 2.0 de este esquema es compatible con los elementos adicionales de localización.

## <a name="language-pack-schema"></a>Esquema del paquete de idioma

El elemento raíz del archivo de paquete de idioma es `<PackageLanguagePackManifest>`, con un atributo de `Version`, que es la versión del formato de paquete de idioma. En este artículo se describe la versión 2.0 del formato de paquete de idioma, que se especifica en el manifiesto estableciendo el `Version` en el valor `Version="2.0.0"`. El elemento raíz contiene exactamente un elemento secundario `<Metadata>` elemento.

### <a name="packagelanguagepackmanifest-element"></a>Elemento PackageLanguagePackManifest

Dentro de la `<PackageLanguagePackManifest>` elemento debe existir el elemento siguiente:

|Título|Descripción|
|-----------|-----------------|
|`<Metadata>`| El elemento contenedor para todos los metadatos de paquete localizado

### <a name="metadata-element"></a>Elemento de metadatos

Dentro de la `<Metadata>` elemento puede tener los siguientes elementos:

|Título|Descripción|
|-----------|-----------------|
|`<DisplayName>`|El nombre localizado de la extensión que se instalará|
|`<Description>`|La descripción adaptada de la extensión que se instalará|
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

|Título|Descripción|
|-----------|-----------------|
|[Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Muestra cómo proporcionar soporte de instalación localizada para un paquete VSIX.|
|[Referencia de esquema 2.0 de extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifiesto VSIX describe el contenido de un *.vsix* archivo de implementación. El archivo de implementación le permite instalar una extensión de Visual Studio mediante el **extensiones y actualizaciones** cuadro de diálogo.|
|[Búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Se muestra cómo usar el **extensiones y actualizaciones** cuadro de diálogo para instalar, quitar, activar y desactivar extensiones.|
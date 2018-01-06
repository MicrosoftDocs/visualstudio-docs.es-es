---
title: Referencia de esquema 2.0 de paquete de idioma VSIX | Documentos de Microsoft
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
caps.latest.revision: "8"
ms.author: dagriffe
author: dgriffen
manager: ghogen
ms.workload: dagriffe
ms.openlocfilehash: b601653e4b2d309d41f32ff71666567ab860e698
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-language-pack-schema-20-reference"></a>Referencia de esquema 2.0 de VSIX Language Pack

El esquema del paquete de idioma de VSIX proporciona información de instalación localizada para los paquetes VSIX. La versión 2.0 de este esquema admite elementos adicionales de localización.

## <a name="language-pack-schema"></a>Esquema del paquete de idioma

El elemento raíz del archivo de paquete de idioma es `<PackageLanguagePackManifest>`, con un atributo de `Version`, que es la versión del formato de paquete de idioma. Este tema describe la versión 2.0 del formato de paquete de idioma, que se especifica en el manifiesto estableciendo la `Version` en el valor `Version="2.0.0"`. El elemento raíz contiene exactamente un elemento secundario `<Metadata>` elemento.

### <a name="packagelangaugepackmanifest-element"></a>Elemento PackageLangaugePackManifest

En el `<PackageLanguagePackManifest>` elemento debe existir el elemento siguiente:
|Title|Descripción|
|-----------|-----------------|
|`<Metadata>`| El elemento contenedor para todos los metadatos de paquete localizado

### <a name="metadata-element"></a>Elemento de metadatos

En el `<Metadata>` elemento puede tener los siguientes elementos:
|Title|Descripción|
|-----------|-----------------|
|`<DisplayName>`|El nombre localizado de la extensión que se va a instalar|
|`<Description>`|La descripción localizada de la extensión que se va a instalar|
|`<License>`| Una ruta de acceso a una versión localizada de la licencia de la extensión|
|`<MoreInfo>`| Un vínculo a información localizada sobre la extensión|
|`<ReleaseNotes>`| Una ruta de acceso o un vínculo a una versión traducida de las notas|
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

|Title|Descripción|
|-----------|-----------------|
|[Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Muestra cómo proporcionar compatibilidad con la instalación localizada para un paquete VSIX.|
|[Referencia de esquema 2.0 de la extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifiesto VSIX describe el contenido de un archivo de implementación .vsix, que permite que una extensión de Visual Studio para instalarse mediante el **extensiones y actualizaciones** cuadro de diálogo.|
|[Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Muestra cómo utilizar el **extensiones y actualizaciones** cuadro de diálogo para instalar, quitar, activar y desactivar extensiones.|
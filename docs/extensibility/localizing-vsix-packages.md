---
title: Localizar paquetes VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 171c8635c2d6db2c346fb836701e630812ecbb28
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186441"
---
# <a name="localizing-vsix-packages"></a>Adaptación de paquetes VSIX

Puede localizar un paquete VSIX mediante la creación de un archivo *Extension. vsixlangpack* para cada idioma de destino y, a continuación, colocarlos en la carpeta correcta. Cuando se instala un paquete localizado, el nombre localizado de la extensión se muestra junto con una descripción traducida. Si proporciona un archivo de licencia localizado, o una dirección URL que apunta a información localizada, también se muestran.

Si el contenido del paquete VSIX incluye un VSPackage que agrega comandos de menú u otra interfaz de usuario, consulte [comandos de menú localizar](../extensibility/localizing-menu-commands.md) para obtener información sobre la localización de los nuevos elementos de la interfaz de usuario.

## <a name="directory-structure"></a>Estructura de directorios

 Cuando un usuario instala una extensión, **extensions and updates** comprueba el nivel superior del paquete VSIX para una carpeta cuyo nombre coincide con la configuración regional de Visual Studio del equipo de destino. Si **extensiones y actualizaciones** encuentra un archivo *. vsixlangpack* en la carpeta, sustituye los valores localizados en ese archivo por los valores correspondientes en el archivo *. vsixmanifest* . Estos valores se muestran cuando se instala la extensión. En el ejemplo siguiente se muestra la estructura de directorios de un paquete VSIX que está localizado en Español (es-ES) y francés (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Las plantillas de proyecto compatibles con VSIX en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generar un manifiesto VSIX y asignarle el nombre *source. Extension. vsixmanifest*. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension. VsixManifest en el paquete VSIX.

## <a name="the-extensionvsixlangpack-file"></a>El archivo Extension. vsixlangpack

El archivo *Extension. vsixlangpack* sigue el [esquema del paquete de idioma de VSIX 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Este esquema tiene un `PackageLanguagePackManifest`, que va seguido inmediatamente de un elemento secundario `Metadata`. El elemento metadata puede contener hasta seis elementos secundarios, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`y `Icon`. Estos elementos secundarios se corresponden con los elementos secundarios `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`y `Icon` del elemento `Metadata` del archivo *Extension. vsixmanifest* .

Al crear un archivo vsixlangpack, debe establecer la propiedad `Include in Vsix` en `true`. De lo contrario, se omitirá el texto de la instalación localizada.

### <a name="to-set-the-include-in-vsix-property"></a>Para establecer la propiedad incluir en VSIX

1. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo Extension. vsixlangpack y, a continuación, haga clic en **propiedades**.

2. En la **cuadrícula de propiedades**, haga clic en **incluir en VSIX**y establezca su valor en `true`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se muestran las partes relevantes de un archivo *Extension. vsixmanifest* . El archivo también incluye el archivo *Extension. vsixlangpack* correspondiente para español. Los valores del paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.

### <a name="code"></a>Código

- [*Extension. vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extensión. vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
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
|[Referencia del esquema del paquete de idioma VSIX 2,0](vsix-language-pack-schema-2-0-reference.md)|Un paquete de idioma VSIX describe la información de localización de un archivo de implementación. vsix.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe la estructura y el contenido de un paquete VSIX.|
|[Localizar comandos de menú](../extensibility/localizing-menu-commands.md)|Muestra cómo localizar otros recursos de texto en una extensión.|
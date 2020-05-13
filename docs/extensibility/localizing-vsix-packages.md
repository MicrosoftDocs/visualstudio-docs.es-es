---
title: Localización de paquetes VSIX ? Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702900"
---
# <a name="localizing-vsix-packages"></a>Adaptación de paquetes VSIX

Puede localizar un paquete VSIX creando un archivo *Extension.vsixlangpack* para cada idioma de destino y, a continuación, colgándolos en la carpeta correcta. Cuando se instala un paquete localizado, el nombre localizado de la extensión se muestra junto con una descripción localizada. Si proporciona un archivo de licencia localizado o una dirección URL que apunta a información localizada, también se muestran.

Si el contenido del paquete VSIX incluye un VSPackage que agrega comandos de menú u otra interfaz de usuario, vea [localizar comandos](../extensibility/localizing-menu-commands.md) de menú para obtener información sobre cómo localizar los nuevos elementos de interfaz de usuario.

## <a name="directory-structure"></a>Estructura de directorios

 Cuando un usuario instala una extensión, **Extensiones y actualizaciones** comprueba el nivel superior del paquete VSIX para una carpeta cuyo nombre coincide con la configuración regional de Visual Studio del equipo de destino. Si **Extensiones y actualizaciones** encuentra un archivo *.vsixlangpack* en la carpeta, sustituye los valores localizados de ese archivo por los valores correspondientes en el archivo *.vsixmanifest.* Estos valores se muestran cuando se instala la extensión. En el ejemplo siguiente se muestra la estructura de directorios de un paquete VSIX que está localizado en español (es-ES) y francés (fr-FR).

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
> Las plantillas de proyecto compatibles [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] con VSIX en el manifiesto generar VSIX y asísaber, asílo se llama *source.extension.vsixmanifest*. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension.VsixManifest en el paquete VSIX.

## <a name="the-extensionvsixlangpack-file"></a>El archivo Extension.vsixlangpack

El archivo *Extension.vsixlangpack* sigue el esquema 2.0 del paquete de [idioma VSIX.](../extensibility/vsix-language-pack-schema-2-0-reference.md) Este esquema `PackageLanguagePackManifest`tiene un , que `Metadata` va seguido inmediatamente de un elemento secundario. El elemento Metadata puede contener hasta `DisplayName` `Description`6 `MoreInfo` `License`elementos secundarios, , , , `ReleaseNotes`, y `Icon`. Estos elementos secundarios `DisplayName` `Description`corresponden `MoreInfo` `License`a `ReleaseNotes`los `Icon` elementos `Metadata` , , , , , , , y secundarios del elemento del archivo *Extension.vsixmanifest.*

Al crear un archivo vsixlangpack, `Include in Vsix` debe `true`establecer la propiedad en . De lo contrario, se omitirá el texto de instalación localizado.

### <a name="to-set-the-include-in-vsix-property"></a>Para establecer la propiedad Incluir en Vsix

1. En el **Explorador**de soluciones , haga clic con el botón secundario en el archivo Extension.vsixlangpack y, a continuación, haga clic en **Propiedades**.

2. En la **cuadrícula de**propiedades , haga clic en Incluir **en Vsix**y establezca su valor en `true`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se muestran partes relevantes de un archivo *Extension.vsixmanifest.* El archivo también incluye el archivo *Extension.vsixlangpack* correspondiente para español. Los valores del paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.

### <a name="code"></a>Código

- [*Extension.vsixmanifest*]

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

- [*Extension.vsixlangpack*]

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
|[Referencia del esquema 2.0 del paquete de idioma VSIX](vsix-language-pack-schema-2-0-reference.md)|Un paquete de idioma VSIX describe la información de localización de un archivo de implementación .vsix.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe la estructura y el contenido de un paquete vsix.|
|[Localizar comandos de menú](../extensibility/localizing-menu-commands.md)|Muestra cómo localizar otros recursos de texto en una extensión.|

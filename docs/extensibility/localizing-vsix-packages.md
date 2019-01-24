---
title: Adaptación de paquetes VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d554819c8c615dc9f8fcd41bb4b460482e21fde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956938"
---
# <a name="localizing-vsix-packages"></a>Adaptación de paquetes VSIX

Puede localizar un paquete VSIX mediante la creación de un *Extension.vsixlangpack* para cada idioma de destino de archivo y, a continuación, colocarlos en la carpeta correcta. Cuando se instala un paquete localizado, se muestra el nombre localizado de la extensión junto con una descripción traducida. Si proporciona un archivo de licencia localizada o una dirección URL que apunta a la información localizada, también se muestran.

Si el contenido de su paquete VSIX incluye un VSPackage que agrega los comandos de menú o de otra interfaz de usuario, consulte [localizar los comandos de menú](../extensibility/localizing-menu-commands.md) para obtener información sobre cómo adaptar los nuevos elementos de interfaz de usuario.

## <a name="directory-structure"></a>Estructura de directorios

 Cuando un usuario instala una extensión, **extensiones y actualizaciones** comprueba el nivel superior del paquete VSIX para una carpeta cuyo nombre coincida con la configuración regional de Visual Studio del equipo de destino. Si **extensiones y actualizaciones** busca un *vsixlangpack* archivo en la carpeta, sustituye los valores traducidos en ese archivo para los valores correspondientes en el *.vsixmanifest*archivo. Estos valores se muestran cuando se está instalando la extensión. El ejemplo siguiente muestra la estructura de directorios para un paquete VSIX que está traducido a español (es-es) y francés (fr-FR).  

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
> Las plantillas de proyecto VSIX admitido en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generar un manifiesto VSIX y asígnele el nombre *source.extension.vsixmanifest*. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension.VsixManifest del paquete VSIX.

## <a name="the-extensionvsixlangpack-file"></a>El archivo Extension.vsixlangpack

El *Extension.vsixlangpack* archivo sigue el [esquema del paquete de idioma VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Este esquema tiene un `PackageLanguagePackManifest`, que va seguido inmediatamente por un `Metadata` elemento secundario. El elemento de metadatos puede contener hasta 6 elementos secundarios, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, y `Icon`. Estos elementos secundarios se corresponden con los `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, y `Icon` elementos secundarios de la `Metadata` elemento de la *Extension.vsixmanifest*archivo.

Cuando se crea un archivo vsixlangpack, debe establecer el `Include in Vsix` propiedad `true`. En caso contrario, se omitirá el texto de instalación localizada.

### <a name="to-set-the-include-in-vsix-property"></a>Para establecer el archivo de inclusión en la propiedad de Vsix

1. En **el Explorador de soluciones**, haga clic en el archivo Extension.vsixlangpack y, a continuación, haga clic en **propiedades**.

2.  En el **cuadrícula de propiedades**, haga clic en **incluir en Vsix**y establezca su valor en `true`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente muestra las partes relevantes de un *Extension.vsixmanifest* archivo. El archivo también incluye el correspondiente *Extension.vsixlangpack* archivo para español. Los valores desde el paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.

### <a name="code"></a>Código

 [*Extension.vsixmanifest*]

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

 [*Extension.vsixlangpack*]

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

|Título|Descripción|
|-----------|-----------------|
|[Referencia de esquema 2.0 de paquete de idioma de VSIX](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|Un paquete de idioma VSIX describe la información de localización de un archivo de implementación de VSIX.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe la estructura y contenido de un paquete vsix.|
|[Localizar los comandos de menú](../extensibility/localizing-menu-commands.md)|Muestra cómo localizar a otros recursos de texto en una extensión.|
---
title: Adaptar paquetes VSIX | Documentos de Microsoft
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a8bb9332b30e5dbc410bdacea3800713b25b10f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-vsix-packages"></a>Adaptar paquetes VSIX

Puede localizar un paquete VSIX creando un archivo Extension.vsixlangpack para cada idioma de destino y, a continuación, colocarlos en la carpeta correcta. Cuando se instala un paquete adaptado, el nombre localizado de la extensión se muestra junto con una descripción traducida. Si se proporciona un archivo de licencia localizada o una dirección URL que apunta a información traducida, también se muestran.

Si el contenido el paquete VSIX incluye un VSPackage que agrega comandos de menú u otra interfaz de usuario, consulte [localizar comandos de menú](../extensibility/localizing-menu-commands.md) para obtener información sobre cómo adaptar los nuevos elementos de interfaz de usuario.

## <a name="directory-structure"></a>Estructura de directorios

 Cuando un usuario instala una extensión, **extensiones y actualizaciones** comprueba el nivel superior del paquete VSIX para una carpeta cuyo nombre coincida con la configuración regional de Visual Studio del equipo de destino. Si **extensiones y actualizaciones** encuentra una vsixlangpack de archivos en la carpeta, sustituye los valores traducidos de los valores correspondientes en el archivo .vsixmanifest en ese archivo. Estos valores se muestran cuando se instala la extensión. En el ejemplo siguiente se muestra la estructura de directorios para un paquete VSIX que está traducido a español (es-es) y francés (fr-FR).  

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
> Las plantillas de proyecto de VSIX admitidos en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generar un manifiesto VSIX y asígnele el nombre source.extension.vsixmanifest. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension.VsixManifest del paquete VSIX.

## <a name="the-extensionvsixlangpack-file"></a>El archivo Extension.vsixlangpack

El archivo Extension.vsixlangpack sigue el [esquema de paquete de idioma de VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Este esquema tiene un `PackageLanguagePackManifest`, que va seguido inmediatamente por un `Metadata` elemento secundario. El elemento de metadatos puede contener hasta 6 elementos secundarios, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, y `Icon`. Estos elementos secundarios corresponden a la `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, y `Icon` elementos secundarios de la `Metadata` elemento del archivo Extension.vsixmanifest.

Cuando se crea un archivo vsixlangpack, debe establecer el `Include in Vsix` propiedad `true`. En caso contrario, se omitirá el texto de instalación localizada.

### <a name="to-set-the-include-in-vsix-property"></a>Para establecer la inclusión en la propiedad de Vsix

1. En **el Explorador de soluciones**, haga clic en el archivo Extension.vsixlangpack y, a continuación, haga clic en **propiedades**.

2.  En la cuadrícula de propiedades, haga clic en **incluir en Vsix**y establezca su valor en `true`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente muestra las partes relevantes de un archivo Extension.vsixmanifest, junto con el archivo Extension.vsixlangpack correspondiente para español. Los valores desde el paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.

### <a name="code"></a>Código

 [Extension.vsixmanifest]

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

 [Extension.vsixlangpack]

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
|[Referencia de esquema 2.0 de paquete de idioma VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Un paquete de idioma VSIX describe la información de localización de un archivo de implementación de VSIX.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe la estructura y el contenido de un paquete vsix.|
|[Adaptación de comandos de menú](../extensibility/localizing-menu-commands.md)|Muestra cómo localizar otros recursos de texto en una extensión.|
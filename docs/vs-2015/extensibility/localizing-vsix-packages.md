---
title: Adaptación de paquetes VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f6bc666e244fed2bc2922ce4878434730a643e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750588"
---
# <a name="localizing-vsix-packages"></a>Adaptación de paquetes VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede localizar un paquete VSIX creando un archivo Extension.vsixlangpack para cada idioma de destino y, a continuación, colocarlos en la carpeta correcta. Cuando se instala un paquete localizado, se muestra el nombre localizado de la extensión junto con una descripción traducida. Si proporciona un archivo de licencia localizada o una dirección URL que apunta a la información localizada, también se muestran.  
  
 Si el contenido de su paquete VSIX incluye un VSPackage que agrega los comandos de menú o de otra interfaz de usuario, consulte [localizar los comandos de menú](../extensibility/localizing-menu-commands.md) para obtener información sobre cómo adaptar los nuevos elementos de interfaz de usuario.  
  
## <a name="directory-structure"></a>Estructura de directorios  
 Cuando un usuario instala una extensión, **extensiones y actualizaciones** comprueba el nivel superior del paquete VSIX para una carpeta cuyo nombre coincida con la configuración regional de Visual Studio del equipo de destino. Si **extensiones y actualizaciones** encuentra un vsixlangpack de archivos en la carpeta, sustituye los valores traducidos en ese archivo para los valores correspondientes en el archivo .vsixmanifest. Estos valores se muestran cuando se está instalando la extensión. El ejemplo siguiente muestra la estructura de directorios para un paquete VSIX que está traducido a español (es-es) y francés (fr-FR).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Las plantillas de proyecto VSIX admitido en el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generar un manifiesto VSIX y asígnele el nombre source.extension.vsixmanifest. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension.VsixManifest del paquete VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>El archivo Extension.vsixlangpack  
 El archivo Extension.vsixlangpack sigue el [esquema del paquete de idioma de VSIX](../extensibility/vsx-language-pack-schema-reference.md). Este esquema tiene un [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) elemento raíz y estos cuatro elementos secundarios: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), y [licencia](../extensibility/license-element-vsix-language-pack-schema.md). Estos elementos secundarios se corresponden con los `Name`, `Description`, `MoreInfoURL`, y `License` elementos secundarios de la `Identifier` elemento del archivo Extension.vsixmanifest.  
  
 Cuando se crea un archivo vsixlangpack, debe establecer el `Include in Vsix` propiedad `true`. En caso contrario, se omitirá el texto de instalación localizada.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Para establecer el archivo de inclusión en la propiedad de Vsix  
  
1.  En **el Explorador de soluciones**, haga clic en el archivo Extension.vsixlangpack y, a continuación, haga clic en **propiedades**.  
  
2.  En la cuadrícula de propiedades, haga clic en **incluir en Vsix**y establezca su valor en `true`.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente muestra las partes relevantes de un archivo Extension.vsixmanifest, junto con el archivo Extension.vsixlangpack correspondiente para español. Los valores desde el paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.  
  
### <a name="code"></a>Código  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento del paquete de idioma VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md)


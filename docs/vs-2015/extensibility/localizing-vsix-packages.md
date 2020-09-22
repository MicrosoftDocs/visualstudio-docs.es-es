---
title: Localizar paquetes VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842586"
---
# <a name="localizing-vsix-packages"></a>Adaptación de paquetes VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede localizar un paquete VSIX mediante la creación de un archivo Extension. vsixlangpack para cada idioma de destino y, a continuación, colocarlos en la carpeta correcta. Cuando se instala un paquete localizado, el nombre localizado de la extensión se muestra junto con una descripción traducida. Si proporciona un archivo de licencia localizado, o una dirección URL que apunta a información localizada, también se muestran.  
  
 Si el contenido del paquete VSIX incluye un VSPackage que agrega comandos de menú u otra interfaz de usuario, consulte [localizar comandos de menú](../extensibility/localizing-menu-commands.md) para obtener información sobre la localización de los nuevos elementos de la interfaz de usuario.  
  
## <a name="directory-structure"></a>Estructura de directorios  
 Cuando un usuario instala una extensión, **extensions and updates** comprueba el nivel superior del paquete VSIX para una carpeta cuyo nombre coincide con la configuración regional de Visual Studio del equipo de destino. Si **extensiones y actualizaciones** encuentra un archivo. vsixlangpack en la carpeta, sustituye los valores localizados en ese archivo por los valores correspondientes en el archivo. vsixmanifest. Estos valores se muestran cuando se instala la extensión. En el ejemplo siguiente se muestra la estructura de directorios de un paquete VSIX que está localizado en Español (es-ES) y francés (fr-FR).  
  
 MyExtension.dll  
  
 Extension. vsixmanifest  
  
 [Content_Types]. XML  
  
 es-ES  
  
 Extensión. vsixlangpack  
  
 fr-FR  
  
 Extensión. vsixlangpack  
  
> [!NOTE]
> Las plantillas de proyecto compatibles con VSIX en el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generar un manifiesto VSIX y nombrarlo Source. Extension. vsixmanifest. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension. VsixManifest en el paquete VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>El archivo Extension. vsixlangpack  
 El archivo Extension. vsixlangpack sigue el [esquema del paquete de idioma de VSIX](../extensibility/vsx-language-pack-schema-reference.md). Este esquema tiene un elemento raíz [del](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) y estos cuatro elementos secundarios: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)y [License](../extensibility/license-element-vsix-language-pack-schema.md). Estos elementos secundarios se corresponden con `Name` los `Description` `MoreInfoURL` elementos secundarios,, y `License` del `Identifier` elemento del archivo Extension. vsixmanifest.  
  
 Al crear un archivo vsixlangpack, debe establecer la `Include in Vsix` propiedad en `true` . De lo contrario, se omitirá el texto de la instalación localizada.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Para establecer la propiedad incluir en VSIX  
  
1. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo Extension. vsixlangpack y, a continuación, haga clic en **propiedades**.  
  
2. En la cuadrícula de propiedades, haga clic en **incluir en VSIX**y establezca su valor en `true` .  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestran las partes relevantes de un archivo Extension. vsixmanifest, junto con el archivo Extension. vsixlangpack correspondiente para el español. Los valores del paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.  
  
### <a name="code"></a>Código  
 [Extension. vsixmanifest]  
  
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
  
 [Extensión. vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Elemento de VSIX LanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md)

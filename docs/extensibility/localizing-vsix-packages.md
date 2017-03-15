---
title: "Adaptar paquetes VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adaptar paquete"
  - "adaptar extensión"
  - "Implementación localizada"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Adaptar paquetes VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede adaptar un paquete VSIX creando un archivo Extension.vsixlangpack para cada idioma de destino y, a continuación, colocarlos en la carpeta correcta. Cuando se instala un paquete adaptado, el nombre localizado de la extensión se muestra junto con una descripción traducida. Si proporciona un archivo de licencia localizada o una dirección URL que señala a información traducida, también se muestran.  
  
 Si el contenido de su paquete VSIX incluye un VSPackage que agrega comandos de menú o de otras interfaces de usuario, consulte [Localizar los comandos de menú](../extensibility/localizing-menu-commands.md) para obtener información sobre cómo adaptar los nuevos elementos de interfaz de usuario.  
  
## Estructura de directorios  
 Cuando un usuario instala una extensión **extensiones y actualizaciones** comprueba el nivel superior del paquete VSIX una carpeta cuyo nombre coincida con la configuración regional de Visual Studio del equipo de destino. Si **extensiones y actualizaciones** encuentra una vsixlangpack de archivo en la carpeta, sustituye los valores traducidos en los valores correspondientes en el archivo .vsixmanifest en ese archivo. Estos valores se muestran cuando se instala la extensión. En el ejemplo siguiente se muestra la estructura de directorios para un paquete VSIX que está traducido a español \(es\-es\) y francés \(fr\-FR\).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 \[Content\_Types\] .xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Las plantillas de proyecto de VSIX admitidos en el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generar un manifiesto VSIX y asígnele el nombre source.extension.vsixmanifest. Cuando Visual Studio compila el proyecto, copia el contenido de ese archivo en Extension.VsixManifest del paquete VSIX.  
  
## El archivo Extension.vsixlangpack  
 El archivo Extension.vsixlangpack sigue el [esquema del paquete de idioma VSIX](../extensibility/vsx-language-pack-schema-reference.md). Este esquema tiene un [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) elemento raíz y estos cuatro elementos secundarios: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [URL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), y [licencia](../extensibility/license-element-vsix-language-pack-schema.md). Estos elementos secundarios corresponden a la `Name`, `Description`, `MoreInfoURL`, y `License` elementos secundarios de la `Identifier` elemento del archivo Extension.vsixmanifest.  
  
 Cuando se crea un archivo vsixlangpack, debe establecer el `Include in Vsix` propiedad `true`. De lo contrario, se omitirá el texto de instalación localizado.  
  
#### Para establecer la incluir en Vsix propiedad  
  
1.  En **el Explorador de soluciones**, haga clic en el archivo Extension.vsixlangpack y, a continuación, haga clic en **propiedades**.  
  
2.  En la cuadrícula de propiedades, haga clic en **incluir en Vsix**, y establezca su valor en `true`.  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente muestra las partes relevantes de un archivo Extension.vsixmanifest, junto con el archivo Extension.vsixlangpack correspondiente para español. Los valores desde el paquete de idioma reemplazan los valores del manifiesto si la configuración regional de Visual Studio del equipo de destino está establecida en español.  
  
### Código  
 \[Extension.vsixmanifest\]  
  
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
  
 \[Extension.vsixlangpack\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## Vea también  
 [Elemento del paquete de idioma VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md)
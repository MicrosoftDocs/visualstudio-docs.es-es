---
title: "&lt;Strings&gt; (Elemento, Arranque) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Strings> (elemento) [arranque]"
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# &lt;Strings&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define las cadenas localizadas de nombres de productos y paquetes, así como mensajes de error de instalación.  
  
## Sintaxis  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## Elementos y atributos  
 El elemento `Strings` es un elemento secundario del elemento `Package`.  No tiene atributos.  
  
## Cadena.  
 El elemento `String` es un elemento secundario del elemento `Strings`.  Un elemento `Strings` puede tener uno o más elementos `String`.  
  
 `String` tiene el atributo siguiente.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Obligatorio.  Nombre de la cadena.|  
  
## Ejemplo  
 En el siguiente ejemplo de código se especifican todas las cadenas en inglés para el instalador de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<Strings>  
    <String Name="DisplayName">.NET Framework 2.0</String>  
    <String Name="Culture">en</String>  
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
</Strings>  
```  
  
## Vea también  
 [\<Package\> \(Elemento\)](../deployment/package-element-bootstrapper.md)
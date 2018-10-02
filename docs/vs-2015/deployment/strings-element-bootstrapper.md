---
title: '&lt;Cadenas&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 76946d04bb8afbe70c599516fc110fcccc8f87c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580095"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Cadenas&gt; (elemento, arranque)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ &lt;cadenas&gt; (elemento, arranque)](https://docs.microsoft.com/visualstudio/deployment/strings-element-bootstrapper).  
  
Define las cadenas localizadas para los nombres de productos, nombres de paquete y los mensajes de error de instalación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `Strings` es un elemento secundario de la `Package` elemento. No tiene atributos.  
  
## <a name="string"></a>String  
 El `String` es un elemento secundario de la `Strings` elemento. Un `Strings` elemento puede tener uno o más `String` elementos.  
  
 `String` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. El nombre de la cadena.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente especifica todas las cadenas en inglés para el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] instalador.  
  
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
  
## <a name="see-also"></a>Vea también  
 [\<Paquete > elemento](../deployment/package-element-bootstrapper.md)




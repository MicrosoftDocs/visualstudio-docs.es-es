---
title: Novedades de MSBuild 12.0 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: d299c4959ddf23a8c249f5577ee03fda99e636f7
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-msbuild-120"></a>Novedades de MSBuild 12.0
MSBuild ahora se instala como parte de Visual Studio en lugar de como parte de .NET Framework. El número de versión actual de MSBuild es 12.0. Si quiere instalar MSBuild por separado, descargue el paquete de instalación desde la página de [descarga de MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  
  
## <a name="changed-path"></a>Ruta de acceso cambiada  
 MSBuild ahora se instala directamente en *%ProgramFiles%*, por ejemplo, en C:\Program Files\MSBuild\\.  
  
## <a name="changed-properties"></a>Propiedades cambiadas  
 Las siguientes propiedades de MSBuild se han modificado como resultado del nuevo número de versión:  
  
-   `MSBuildToolsVersion` para esta versión de herramientas es 12.0.  
  
-   `MSBuildToolsPath` es ahora %ProgramFiles%\MSBuild\12.0\bin en sistemas operativos de 32 bits, o %ProgramFiles%\MSBuild\12.0\bin\amd64 en sistemas operativos de 64 bits.  
  
-   Los valores de `ToolsVersion` se encuentran en HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 para sistemas operativos de 32 bits o HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 para sistemas operativos de 64 bits.  
  
-   Las propiedades `SDK35ToolsPath` y `SDK40ToolsPath` apuntan al .NET Framework SDK que se incluye con esta versión de Visual Studio (por ejemplo, 8.1A para la versión 4.X de las herramientas).  
  
## <a name="new-properties"></a>Propiedades nuevas  
  
-   `MSBuildFrameworkToolsPath` es una nueva propiedad con un valor de %windir%\Microsoft.NET\Framework\v4.0.30319 en sistemas operativos de 32 bits o de %windir%\Microsoft.NET\Framework64\v4.0.30319 en sistemas operativos de 64 bits. Es un reemplazo para `MSBuildToolsPath` que se puede usar para señalar a las herramientas y utilidades de .NET Framework.  
  
-   `MSBuildToolsPath` y `MSBuildFrameworkToolsPath` tienen sus equivalentes de 32 bits, `MSBuildToolsPath32` y `MSBuildFrameworkToolsPath32`, que siempre apuntan a la ubicación de 32 bits, independientemente de si se está usando MSBuild de 32 o de 64 bits.

## <a name="see-also"></a>Vea también
[MSBuild](../msbuild/msbuild.md)

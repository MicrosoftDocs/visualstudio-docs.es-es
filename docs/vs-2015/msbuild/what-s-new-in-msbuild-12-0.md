---
title: Novedades de MSBuild 12.0 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d91ec9044461cf57bba8bb36a0d2e029635155c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582838"
---
# <a name="what39s-new-in-msbuild-120"></a>Novedades de MSBuild 12.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](https://docs.microsoft.com/visualstudio/).  
  
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
[MSBuild](msbuild.md)



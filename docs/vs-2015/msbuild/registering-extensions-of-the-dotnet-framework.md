---
title: Registrar las extensiones de .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a2d3e281562be5234e0a70a877a6c169c346995
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573942"
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrar las extensiones de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [registrar extensiones de .NET Framework](https://docs.microsoft.com/visualstudio/msbuild/registering-extensions-of-the-dotnet-framework).  
  
  
Puede desarrollar un ensamblado que extienda una versión concreta de .NET Framework. Para que el ensamblado se muestre en el cuadro de diálogo **Agregar referencias** de Visual Studio, debe agregar la carpeta que lo contiene al registro del sistema.  
  
 Por ejemplo, suponga que la empresa Trey Research ha desarrollado una biblioteca que extiende .NET Framework 4, y quiere que los ensamblados de biblioteca se muestren en el cuadro de diálogo **Agregar referencias** cuando un proyecto tiene como destino .NET Framework 4. Suponga también que los ensamblados son ensamblados de 32 bits que se ejecutan en un equipo de 32 bits o ensamblados de 64 bits que se ejecutan en un equipo de 64 bits, y que se instalarán en la carpeta C:\TreyResearch\Extensions4\.  
  
 Registre esta carpeta mediante esta clave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Dé a la clave este valor predeterminado: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
>  El número de compilación de la versión de .NET Framework puede ser diferente.  
  
 Para registrar un ensamblado de 32 bits en un equipo de 64 bits, utilice el nodo Wow6432, por ejemplo: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Vea también  
 [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)




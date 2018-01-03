---
title: Registrar las extensiones de .NET Framework | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 5e9ab37b054dd137590b38dcd62d2de7ebdd1cd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrar las extensiones de .NET Framework
Puede desarrollar un ensamblado que extienda una versión concreta de .NET Framework. Para que el ensamblado se muestre en el cuadro de diálogo **Agregar referencias** de Visual Studio, debe agregar la carpeta que lo contiene al registro del sistema.  
  
 Por ejemplo, suponga que la empresa Trey Research ha desarrollado una biblioteca que extiende .NET Framework 4, y quiere que los ensamblados de biblioteca se muestren en el cuadro de diálogo **Agregar referencias** cuando un proyecto tiene como destino .NET Framework 4. Suponga también que los ensamblados son ensamblados de 32 bits que se ejecutan en un equipo de 32 bits o ensamblados de 64 bits que se ejecutan en un equipo de 64 bits, y que se instalarán en la carpeta C:\TreyResearch\Extensions4\.  
  
 Registre esta carpeta mediante esta clave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Dé a la clave este valor predeterminado: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
>  El número de compilación de la versión de .NET Framework puede ser diferente.  
  
 Para registrar un ensamblado de 32 bits en un equipo de 64 bits, utilice el nodo Wow6432, por ejemplo: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Vea también  
 [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
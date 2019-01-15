---
title: Registrar las extensiones de .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 48322adffff68d1eecb0d44da7e8f78d39d82203
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986078"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrar las extensiones de .NET Framework
Puede desarrollar un ensamblado que extienda una versión concreta de .NET Framework. Para que el ensamblado se muestre en el cuadro de diálogo **Agregar referencias** de Visual Studio, debe agregar la carpeta que lo contiene al registro del sistema.  
  
 Por ejemplo, suponga que la empresa Trey Research ha desarrollado una biblioteca que extiende .NET Framework 4, y quiere que los ensamblados de biblioteca se muestren en el cuadro de diálogo **Agregar referencias** cuando un proyecto tiene como destino .NET Framework 4. Suponga también que los ensamblados son ensamblados de 32 bits que se ejecutan en un equipo de 32 bits o ensamblados de 64 bits que se ejecutan en un equipo de 64 bits, y que se instalarán en la carpeta *C:\TreyResearch\Extensions4\\\*.  
  
 Registre esta carpeta mediante esta clave: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Asigne a la clave este valor predeterminado: **C:\TreyResearch\Extensions4**.  
  
> [!NOTE]
>  El número de compilación de la versión de .NET Framework puede ser diferente.  
  
 Para registrar un ensamblado de 32 bits en un equipo de 64 bits, use el nodo Wow6432, por ejemplo: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.  
  
### <a name="see-also"></a>Vea también  
 [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
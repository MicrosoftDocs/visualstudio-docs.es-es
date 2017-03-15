---
title: "Registrar las extensiones de .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo Agregar referencias, registro de las extensiones de .NET Framework"
  - "MSBuild, registro de las extensiones de .NET Framework"
  - "extensiones de .NET Framework, registro"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Registrar las extensiones de .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede desarrollar un ensamblado que extienda una versión concreta de .NET Framework.  Para permitir que el ensamblado aparezca en el cuadro de diálogo **Agregar referencias** de Visual Studio, debe agregar la carpeta que lo contiene al Registro del sistema.  
  
 Por ejemplo, supongamos que la compañía Trey Research ha desarrollado una biblioteca que extiende .NET Framework 4, y que desea que los ensamblados de biblioteca aparezcan en el cuadro de diálogo **Agregar referencias** cuando un proyecto esté destinado a .NET Framework 4.  Supongamos, además, que los ensamblados son de 32 bits y se ejecutan en un equipo de 32 bits, o bien que son ensamblados de 64 bits que se ejecutan en un equipo de 64 bits, y que se instalarán en la carpeta C:\\TreyResearch\\Extensions4\\.  
  
 Registre esta carpeta utilizando esta clave: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  Dé a la clave este valor predeterminado: C:\\TreyResearch\\Extensions4.  
  
> [!NOTE]
>  El número de compilación de la versión de .NET Framework puede ser diferente.  
  
 Para registrar un ensamblado de 32 bits en un equipo de 64 bits, utilice el nodo Wow6432; por ejemplo: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  
  
## Vea también  
 [Integración de Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
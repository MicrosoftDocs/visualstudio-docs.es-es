---
title: "Informaci&#243;n general sobre compatibilidad con m&#250;ltiples versiones (multi-targeting) de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Informaci&#243;n general sobre compatibilidad con m&#250;ltiples versiones (multi-targeting) de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con MSBuild, puede compilar una aplicación para que se ejecute en cualquiera de las versiones de .NET Framework, y en cualquiera de las plataformas del sistema.  Por ejemplo, puede compilar una aplicación para que se ejecute en .NET Framework 2.0 en una plataforma de 32 bits y compilar esa misma aplicación para que se ejecute en .NET Framework 4.5 en una plataforma de 64 bits.  
  
> [!IMPORTANT]
>  A pesar del nombre “compatibilidad con múltiples versiones”, un proyecto solo puede tener como destino una versión de Framework y una plataforma al mismo tiempo.  
  
 Estas son algunas de las características de los destinos de MSBuild:  
  
-   Puede desarrollar una aplicación que tenga como destino una versión anterior de .NET Framework, por ejemplo, las versiones 2.0, 3.5 o 4.  
  
-   Puede tener como destino un marco distinto de .NET Framework, por ejemplo, Silverlight.  
  
-   Puede tener como destino un *perfil de Framework*, que es un subconjunto predefinido de una versión de .NET Framework de destino.  
  
-   Si se publica algún Service Pack para la versión actual de .NET Framework, podría utilizarlo como destino.  
  
-   La compatibilidad con múltiples versiones de MSBuild garantiza que una aplicación utilice solo la funcionalidad que está disponible en el marco y plataforma de destino.  
  
## Versión de .NET Framework y plataforma de destino  
 Una *versión de .NET Framework de destino* es la versión de .NET Framework para la que se compila un proyecto, y una *plataforma de destino* es la plataforma del sistema para la que se compila el proyecto.  Por ejemplo, puede que desee diseñar una aplicación de .NET Framework 2.0 para que se ejecute en una plataforma de 32 bits compatible con la familia de procesadores 802x86 \(x86\).  La combinación de la versión de .NET Framework de destino y la plataforma de destino se denomina *contexto de destino*.  Para obtener más información, vea [Versión de .NET Framework de destino y plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## Conjunto de herramientas \(ToolsVersion\)  
 Un conjunto de herramientas recopila las herramientas, las tareas y los destinos que se usan para crear la aplicación.  Un conjunto de herramientas incluye compiladores como csc.exe y vbc.exe, el archivo de destinos comunes \(microsoft.common.targets\) y el archivo de tareas comunes \(microsoft.common.tasks\).  El conjunto de herramientas de la versión 4.5 se puede usar para crear aplicaciones para las versiones 2.0, 3.0, 3.5, 4 y 4.5 de .NET Framework. Sin embargo, el conjunto de herramientas de la versión 2.0 solo se puede usar para las aplicaciones de la versión 2.0 de .NET Framework.  Para obtener más información, vea [Conjunto de herramientas \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Ensamblados de referencia  
 Los ensamblados de referencia que se especifican en el conjunto de herramientas le ayudan a diseñar y compilar una aplicación.  Estos ensamblados de referencia no solo habilitan una compilación de destino determinada, sino que también restringen los componentes y las características del IDE de Visual Studio a aquellos compatibles con el destino.  Para obtener más información, vea [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md)  
  
## Configurar destinos y tareas  
 Puede configurar los destinos y las tareas de MSBuild para que se ejecuten en modo inactivo con MSBuild y así poder tener como destinos contextos considerablemente distintos del que se está ejecutando.  Por ejemplo, puede tener como destino una aplicación de 32 bits de .NET Framework 2.0 mientras el equipo de desarrollo se ejecuta en una plataforma de 64 bits con .NET Framework 4.5. Para obtener más información, vea [Configurar destinos y tareas](../msbuild/configuring-targets-and-tasks.md).  
  
## Solución de problemas  
 Pueden producirse errores si intenta hacer referencia a un ensamblado que no forma parte del contexto de destino.  Para obtener más información sobre estos errores y qué hacer con ellos, vea [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
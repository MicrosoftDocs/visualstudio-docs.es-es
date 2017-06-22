---
title: "Introducción a la compatibilidad con múltiples versiones (multi-targeting) de MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 9c224e926024e99477c81fe4f8c533d59280074d
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="msbuild-multitargeting-overview"></a>Información general sobre compatibilidad con múltiples versiones (multi-targeting) de MSBuild
Con MSBuild, puede compilar una aplicación para que se ejecute en cualquiera de las versiones de .NET Framework, y en cualquiera de las plataformas del sistema. Por ejemplo, puede compilar una aplicación para que se ejecute en .NET Framework 2.0 en una plataforma de 32 bits y compilar esa misma aplicación para que se ejecute en .NET Framework 4.5 en una plataforma de 64 bits.  
  
> [!IMPORTANT]
>  A pesar del nombre "compatibilidad con múltiples versiones", un proyecto solo puede tener como destino una versión de Framework y una plataforma al mismo tiempo.  
  
 Estas son algunas de las características de los destinos de MSBuild:  
  
-   Puede desarrollar una aplicación que tenga como destino una versión anterior de .NET Framework, por ejemplo, las versiones 2.0, 3.5 o 4.  
  
-   Puede tener como destino un marco distinto de .NET Framework, por ejemplo, Silverlight.  
  
-   Puede tener como destino un *perfil de Framework*, que es un subconjunto predefinido de un marco de trabajo de destino.  
  
-   Si se publica algún Service Pack para la versión actual de .NET Framework, podría utilizarlo como destino.  
  
-   La compatibilidad con múltiples versiones de MSBuild garantiza que una aplicación utilice solo la funcionalidad que está disponible en el marco y plataforma de destino.  
  
## <a name="target-framework-and-platform"></a>Versión de .NET Framework y plataforma de destino  
 Una *plataforma de destino* es la versión de .NET Framework para la que se compila un proyecto, y una *plataforma de destino* es la plataforma del sistema para la que se compila el proyecto.  Por ejemplo, puede que desee diseñar una aplicación de .NET Framework 2.0 para que se ejecute en una plataforma de 32 bits compatible con la familia de procesadores 802x86 (x86). La combinación de la plataforma de destino y la plataforma de destino se denomina *contexto de destino*. Para obtener más información, vea [Versión de .NET Framework de destino y plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Conjunto de herramientas (ToolsVersion)  
 Un conjunto de herramientas recopila las herramientas, las tareas y los destinos que se usan para crear la aplicación. Un conjunto de herramientas incluye compiladores como csc.exe y vbc.exe, el archivo de destinos comunes (microsoft.common.targets) y el archivo de tareas comunes (microsoft.common.tasks). El conjunto de herramientas de la versión 4.5 se puede usar para crear aplicaciones para las versiones 2.0, 3.0, 3.5, 4 y 4.5 de .NET Framework. En cambio, el conjunto de herramientas de la versión 2.0 solo se puede usar para las aplicaciones de la versión 2.0 de .NET Framework. Para obtener más información, vea [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Ensamblados de referencia  
 Los ensamblados de referencia que se especifican en el conjunto de herramientas le ayudan a diseñar y compilar una aplicación. Estos ensamblados de referencia no solo habilitan una compilación de destino determinada, sino que también restringen los componentes y las características del IDE de Visual Studio a aquellos compatibles con el destino. Para obtener más información, vea [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="configuring-targets-and-tasks"></a>Configurar destinos y tareas  
 Puede configurar los destinos y las tareas de MSBuild para que se ejecuten en modo inactivo con MSBuild y así poder tener como destinos contextos considerablemente distintos del que se está ejecutando.  Por ejemplo, puede tener como destino una aplicación de 32 bits de .NET Framework 2.0 mientras el equipo de desarrollo se ejecuta en una plataforma de 64 bits con .NET Framework 4.5. Para obtener más información, vea [Configurar destinos y tareas](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Solución de problemas  
 Pueden producirse errores si intenta hacer referencia a un ensamblado que no forma parte del contexto de destino. Para obtener más información sobre estos errores y qué hacer con ellos, vea [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

---
title: Filtrar Establecer configuraciones Debug y Release | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93aa6d9f6e821dba012009e90ba6f9be51641703
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987373"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Filtrar Conjunto de configuraciones Debug y Release
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Como se desprende de sus nombres, la versión de depuración se compila para depurar y la versión de lanzamiento para la distribución final.  
  
 La configuración de depuración del programa se compila sin optimizar y con toda la información de depuración simbólica. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.  
  
 La configuración de lanzamiento del programa no contiene información de depuración simbólica y está totalmente optimizada. La información de depuración se puede generar en archivos PDB, en función de las opciones del compilador utilizadas. Crear archivos PDB puede ser muy útil si luego necesita depurar la versión de lanzamiento.  
  
 Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 Puede cambiar la configuración de compilación desde el **compilar** menú desde la barra de herramientas, o en páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación de proyectos en distintos lenguajes, consulte la sección Temas relacionados que aparece más adelante.  
  
### <a name="to-change-the-build-configuration"></a>Para cambiar la configuración de compilación:  
  
1.  En el menú compilar: haga clic en **compilar / Administrador de configuración**, a continuación, seleccione **depurar** o **versión**.  
  
2.  En la barra de herramientas, elija **depurar** o **versión** desde el **configuraciones de soluciones** cuadro de lista.  
  
     ![configuración de compilación de la barra de herramientas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Esta barra de herramientas no está disponible en las ediciones Express. Puede usar el **compilar solución F6** y **Iniciar depuración F5** elementos de menú para elegir la configuración.  
  
## <a name="see-also"></a>Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)   
 [Configuraciones Debug y Release](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)

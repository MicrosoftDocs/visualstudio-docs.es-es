---
title: 'Cómo: establecer configuraciones Debug y Release | Microsoft Docs'
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
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703656"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Cómo: Establecer configuraciones Debug y Release
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Como se desprende de sus nombres, la versión de depuración se compila para depurar y la versión de lanzamiento para la distribución final.  
  
 La configuración de depuración del programa se compila sin optimizar y con toda la información de depuración simbólica. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.  
  
 La configuración de lanzamiento del programa no contiene información de depuración simbólica y está totalmente optimizada. La información de depuración se puede generar en archivos PDB, en función de las opciones del compilador utilizadas. Crear archivos PDB puede ser muy útil si luego necesita depurar la versión de lanzamiento.  
  
 Para obtener más información sobre las configuraciones de compilación, vea Descripción de las [configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 Puede cambiar la configuración de compilación desde el menú **compilar** , desde la barra de herramientas o en las páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación de proyectos en distintos lenguajes, consulte la sección Temas relacionados que aparece más adelante.  
  
### <a name="to-change-the-build-configuration"></a>Para cambiar la configuración de compilación:  
  
1. En el menú compilar: haga clic en **compilar/Configuration Manager**y, a continuación, seleccione **depurar** o **liberar**.  
  
2. En la barra de herramientas, elija **depurar** o **liberar** en el cuadro de lista **configuraciones de soluciones** .  
  
     ![configuración de la compilación de la barra de herramientas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Esta barra de herramientas no está disponible en las ediciones Express. Puede usar los elementos de menú **compilar solución F6** e **iniciar depuración F5** para elegir la configuración.  
  
## <a name="see-also"></a>Consulte también  
 [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuración del proyecto para las configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración del proyecto para una configuración de depuración Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)   
 [Configuraciones Debug y Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)

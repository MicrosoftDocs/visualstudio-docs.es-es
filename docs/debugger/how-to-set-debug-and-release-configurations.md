---
title: "C&#243;mo: Establecer configuraciones Debug y Release | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.builds"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "configuraciones de compilación, depuración"
  - "configuraciones de compilación, versión"
  - "configuraciones, versión"
  - "compilaciones de depuración"
  - "compilaciones de depuración, cambiar los valores de configuración"
  - "compilaciones de depuración, cambiar a una versión de lanzamiento"
  - "configuraciones de depuración"
  - "depurar [Visual Studio], configuraciones de depuración"
  - "depurar [Visual Studio], configuración de lanzamiento"
  - "proyectos [Visual Studio], configuraciones de depuración"
  - "proyectos [Visual Studio], configuración de lanzamiento"
  - "versiones de lanzamiento, cambiar configuración"
  - "versiones de lanzamiento, cambiar a una versión de depuración"
  - "proyectos de Visual Basic, versiones de depuración y de lanzamiento"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Establecer configuraciones Debug y Release
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa.  Como se desprende de sus nombres, la versión de depuración se compila para depurar y la versión de lanzamiento para la distribución final.  
  
 La configuración de depuración del programa se compila sin optimizar y con toda la información de depuración simbólica.  La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.  
  
 La configuración de lanzamiento del programa no contiene información de depuración simbólica y está totalmente optimizada.  La información de depuración se puede generar en archivos PDB, en función de las opciones del compilador utilizadas.  Crear archivos PDB puede ser muy útil si luego necesita depurar la versión de lanzamiento.  
  
 Para obtener más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
 La configuración de compilación se puede modificar desde el menú **Compilar**, la barra de herramientas o las páginas de propiedades del proyecto.  Las páginas de propiedades del proyecto son específicas de un lenguaje.  El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas.  Para obtener más información sobre cómo cambiar la configuración de compilación de proyectos en distintos lenguajes, consulte la sección Temas relacionados que aparece más adelante.  
  
### Para cambiar la configuración de compilación:  
  
1.  En el menú Compilar: haga clic en **Compilar\/Administrador de configuración** y seleccione **Depurar** o **Versión**.  
  
2.  En la barra de herramientas, elija **Depurar** o **Versión** en el cuadro de lista **Configuraciones de soluciones**.  
  
     ![configuración de la compilación de la barra de herramientas](~/debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Esta barra de herramientas no está disponible en las ediciones Express.  Puede utilizar los elementos de menú **Compilar solución F6** e **Iniciar depuración F5** para elegir la configuración.  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Configuración del proyecto para una configuración de depuración de C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuración del proyecto para configuraciones de depuración en C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e)
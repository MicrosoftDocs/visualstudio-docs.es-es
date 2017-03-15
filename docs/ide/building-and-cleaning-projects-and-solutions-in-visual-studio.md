---
title: "Compilar y limpiar proyectos y soluciones en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.BuildProjectPicker"
  - "vs.batchbuild"
helpviewer_keywords: 
  - "Limpiar solución (comando)"
  - "compilaciones [Visual Studio], administración"
  - "configuraciones de compilación de la solución, inicio"
  - "Compilar solución (comando)"
  - "configuraciones de compilación del proyecto, inicio"
  - "configuraciones de compilación, inicio"
  - "configuraciones de compilación del proyecto, dependencias"
  - "Recompilar solución (comando)"
  - "configuraciones de compilación de la solución, orden de compilación"
  - "compilaciones [Visual Studio], preparación"
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Compilar y limpiar proyectos y soluciones en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mediante los procedimientos de este tema, puede compilar, recompilar, o limpiar todos los o algunos proyectos o elementos de proyecto en una solución.  Para un tutorial paso a paso, vea [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md).  
  
> [!NOTE]
>  La interfaz de usuario en Visual Studio podría diferir de lo que describe este tema, dependiendo de los valores de configuración activos.  Para cambiar la configuración, abra el menú **herramientas**, y elija **Importar y exportar configuraciones**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para compilar, recompilar o limpiar una solución completa  
  
1.  En **Explorador de soluciones**, elija o abra la solución.  
  
2.  En la barra de menú, elija **Compilación**, y elija uno de los siguientes comandos:  
  
    -   Elija **Compilación** o **Generar solución** para compilar sólo los archivos y componentes del proyecto que han cambiado desde la compilación más reciente.  
  
        > [!NOTE]
        >  El comando **Compilar** cambia a **Compilar solución** cuando una solución incluye más de un proyecto.  
  
    -   Elija **Recompilar solución** para “limpiar” la solución y luego compilar todos los archivos y componentes del proyecto.  
  
    -   Elija **Limpiar solución** para eliminar los archivos intermedios y de salida.  Con sólo los archivos del proyecto y componentes que quedan, las nuevas instancias de archivos intermedios y de salida pueden compilar.  
  
### Para compilar o recompilar un solo proyecto  
  
1.  En **Explorador de soluciones**, elija o abra el proyecto.  
  
2.  En la barra de menú, elija **Compilación**, y elija **Compilación***ProjectName* o **Volver a generar***ProjectName*.  
  
    -   Elija **Compilación***ProjectName* para compilar sólo los componentes del proyecto que han cambiado desde la compilación más reciente.  
  
    -   Elija **Volver a generar***ProjectName* para “limpiar” el proyecto y después se compilan los archivos de proyecto y todos los componentes del proyecto.  
  
### Para compilar sólo el proyecto inicial y sus dependencias  
  
1.  En la barra de menú, elija **herramientas**, **opciones**.  
  
2.  En el cuadro de diálogo **opciones**, expanda el nodo **Proyectos y soluciones** y, a continuación la página **Generar y ejecutar**.  
  
     El cuadro de diálogo **Compilar y ejecutar, proyectos y Soluciones, opciones** se abre.  
  
3.  Active la casilla **Generar proyectos de inicio y dependencias únicamente al ejecutar**.  
  
     Cuando se selecciona esta casilla, se compilan sólo el proyecto de inicio actual y sus dependencias al realizar cualquiera de los pasos siguientes:  
  
    -   En la barra de menú, elija **debug**, **Inicio** \(F5\).  
  
    -   En la barra de menú, elija **Compilación**, **Generar solución** \(CTRL\+MAYÚS\+B\).  
  
     Si se desactiva esta casilla, se compilan todos los proyectos, sus dependencias, y los archivos de solución al ejecutar cualquiera de los comandos anteriores.  Esta casilla se encuentra desactivada de forma predeterminada.  
  
### Para compilar sólo el proyecto seleccionado de Visual C\+\+  
  
1.  Elija un proyecto de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] y, a continuación, en la barra de menú, elija **Compilación**, **Sólo proyecto**; uno de los siguientes comandos:  
  
    -   **Compilación solo** *ProjectName*  
  
    -   **Recompile sólo** *ProjectName*  
  
    -   **Limpiar sólo** *ProjectName*  
  
    -   **Vínculo solo** *ProjectName*  
  
     Estos comandos solo se aplican al proyecto de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elegida, sin compilar, recompilar, limpiar, o vincular ninguna dependencia del proyecto o archivo de solución.  Dependiendo de la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], el submenú **Sólo proyecto** puede contener varios comandos.  
  
### Para compilar varios elementos de proyecto de C\+\+  
  
1.  En **Explorador de soluciones**, elija varios archivos que tienen pueden ser acciones de compilación, abra el menú contextual para uno de dichos archivos, y después elija **Compilar**.  
  
     Si los archivos tienen dependencias, los archivos se compilarán en orden de dependencia.  La operación de compilación generará un error si los archivos requieren un encabezado precompilado que no está disponible cuando se compila.  La operación de compilación utiliza la configuración de soluciones activa.  
  
### Para detener una compilación  
  
1.  Realice uno de estos pasos:  
  
    -   En la barra de menú, elija **Compilación**, **cancelar**.  
  
    -   Elija las teclas Ctrl \+ de interrupción.  
  
## Vea también  
 [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e)   
 [Referencia de compilación de C\/C\+\+](/visual-cpp/build/reference/c-cpp-building-reference)   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)
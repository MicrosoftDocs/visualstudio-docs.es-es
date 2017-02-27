---
title: "C&#243;mo: Limitar la instrumentaci&#243;n a archivos DLL espec&#237;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, ventana de control de generación de perfiles en tiempo de ejecución"
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Limitar la instrumentaci&#243;n a archivos DLL espec&#237;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con el método de generación de perfiles de instrumentación, puede limitar la recolección de datos de generación de perfiles a uno o más archivos DLL de una aplicación.  Para generar perfiles de uno o más archivos DLL de una aplicación, se crea una sesión de rendimiento que incluye los archivos .dll como destinos.  Puede especificar los archivos DLL de los que desea generar perfiles como proyectos de una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o como archivos binarios independientes.  
  
### Para limitar la instrumentación a archivos DLL concretos de una solución de Visual Studio  
  
1.  Abra la solución que contiene el archivo DLL en [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.  
  
3.  Elija **Instrumentación** como método de generación de perfiles y, a continuación, haga clic en **Siguiente**.  
  
4.  En **¿Para cuál de los siguientes destinos disponibles desea crear un perfil?**, seleccione el nombre del proyecto .dll y, a continuación, haga clic en **Siguiente**.  
  
5.  Haga clic en **Finalizar** para salir del asistente y mostrar la nueva sesión de rendimiento en la ventana **Explorador de rendimiento**.  
  
6.  Haga clic con el botón secundario en **Destinos** y, a continuación, seleccione **Agregar proyecto de destino**.  
  
7.  En la lista **Agregar proyecto de destino**, seleccione el proyecto ejecutable que desea utilizar para ejecutar el archivo DLL.  
  
     Opcional.  Puede agregar cualquier proyecto DLL adicional del que desee generar perfiles.  
  
8.  Para evitar la recolección de datos de un proyecto agregado, haga clic con el botón secundario en el nombre del proyecto y, a continuación, desactive la casilla **Instrumentar**.  
  
### Para especificar archivos DLL concretos para generar perfiles como binarios independientes  
  
1.  Abra [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.  
  
3.  En **¿Para cuál de los siguientes destinos disponibles desea crear un perfil?**, seleccione **Generar el perfil de una biblioteca de vínculos dinámicos \(.DLL\)** y, a continuación, haga clic en **Siguiente**.  
  
4.  En la segunda página del asistente, realice los pasos siguientes:  
  
    -   Escriba la ruta de acceso y el nombre del archivo .dll del que desea generar perfiles en **Ruta de acceso de archivos DLL**.  También puede hacer clic en el botón de puntos suspensivos \(...\) para buscar el archivo en el cuadro de diálogo **Biblioteca de vínculos dinámicos para la que se va a generar un perfil**.  Tenga en cuenta que debe especificar la copia del archivo .dll que iniciará el archivo ejecutable \(.exe\) que seleccione a continuación.  
  
    -   Escriba la ruta de acceso y el nombre del archivo ejecutable \(.exe\) que ejecutará el archivo .dll en **Ruta de acceso del archivo ejecutable**.  También puede hacer clic en el botón de puntos suspensivos \(...\) para buscar el archivo en el cuadro de diálogo **Ejecutable para iniciar**.  
  
    -   Opcional.  Escriba los argumentos de la línea de comandos que desea pasar al archivo ejecutable en **Argumentos de la línea de comandos**.  Si es necesario, especifique el directorio de trabajo de la aplicación en **Directorio de trabajo**.  
  
    -   Haga clic en **Siguiente**.  
  
5.  Elija **Instrumentación** como método de generación de perfiles y, a continuación, haga clic en **Siguiente**.  
  
6.  Haga clic en **Finalizar** para salir del asistente y mostrar la nueva sesión de rendimiento en la ventana **Explorador de rendimiento**.  
  
7.  Opcional.  Para agregar más archivos .dll, haga clic con el botón secundario en **Destinos** y, a continuación, seleccione **Agregar binario de destino**.  Seleccione los archivos en el cuadro de diálogo **Agregar binario de destino**.  
  
    > [!NOTE]
    >  No especifique el archivo ejecutable \(.exe\) que ejecuta los archivos DLL.  
  
## Vea también  
 [Controlar la recolección de datos](../profiling/controlling-data-collection.md)   
 [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
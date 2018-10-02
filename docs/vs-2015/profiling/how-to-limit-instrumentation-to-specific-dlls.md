---
title: 'Cómo: Limitar la instrumentación a archivos DLL específicos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99a67921739f620c908f1551f0f8a29a5aac73a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566224"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Cómo: Limitar la instrumentación a archivos DLL específicos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: límite de instrumentación a archivos DLL específicos](https://docs.microsoft.com/visualstudio/profiling/how-to-limit-instrumentation-to-specific-dlls).  
  
El método de generación de perfiles de instrumentación permite limitar la recopilación de datos de generación de perfiles a uno o más archivos DLL en una aplicación. Para generar perfiles de uno o más archivos DLL en una aplicación, debe crearse una sesión de rendimiento que incluya los archivos .dll como destinos. Se pueden especificar los archivos DLL de los que se desea generar perfiles como proyectos de una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o como archivos binarios independientes.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Para limitar la instrumentación a archivos DLL específicos en una solución de Visual Studio  
  
1.  Abra la solución que contiene el DLL en [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.  
  
3.  Elija **Instrumentación** como el método de generación de perfiles y después haga clic en **Siguiente**.  
  
4.  En **¿De cuál de los siguientes destinos disponibles desea generar perfiles?**, seleccione el nombre del proyecto .dll y después haga clic en **Siguiente**.  
  
5.  Haga clic en **Finalizar** para salir del asistente y mostrar la nueva sesión de rendimiento en la ventana **Explorador de rendimiento**.  
  
6.  Haga clic en **Destinos** y después seleccione **Agregar proyecto de destino**.  
  
7.  En la lista **Agregar proyecto de destino**, seleccione el proyecto ejecutable que desea utilizar para ejecutar el archivo DLL.  
  
     Opcional. Puede agregar cualquier proyecto DLL del que desee generar perfiles.  
  
8.  Para evitar la recopilación de datos de un proyecto agregado, haga clic con el botón derecho en el nombre del proyecto y después desactive la casilla **Instrumento**.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Para especificar archivos DLL concretos para generar perfiles como binarios independientes  
  
1.  Abra [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.  
  
3.  En **¿De cuál de los siguientes destinos disponibles desea generar perfiles?**, seleccione **Generar perfiles de una biblioteca de vínculos dinámicos (.DLL)** y después haga clic en **Siguiente**.  
  
4.  En la segunda página del asistente, realice los siguientes pasos:  
  
    -   Escriba la ruta de acceso y el nombre del archivo .dll de que desea generar perfiles en **ruta de acceso del archivo Dll**. También puede hacer clic en el botón de puntos suspensivos (...) para buscar el archivo en el cuadro de diálogo **Biblioteca de vínculos dinámicos de la que generar perfiles**. Tenga en cuenta que debe especificar la copia del archivo .dll que será iniciada por el archivo ejecutable (.exe) que seleccione a continuación.  
  
    -   Escriba la ruta de acceso y el nombre del archivo ejecutable (.exe) que ejecutará el archivo .dll en **Ruta ejecutable**. También puede hacer clic en el botón de puntos suspensivos (...) para buscar el archivo en el cuadro de diálogo **Ejecutable para iniciar**.  
  
    -   Opcional. Escriba los argumentos de línea de comandos que desea pasar al archivo ejecutable en **Argumentos de línea de comandos**. Si es necesario, especifique el directorio de trabajo de la aplicación en **Directorio de trabajo**.  
  
    -   Haga clic en **Siguiente**.  
  
5.  Elija **Instrumentación** como el método de generación de perfiles y después haga clic en **Siguiente**.  
  
6.  Haga clic en **Finalizar** para salir del asistente y mostrar la nueva sesión de rendimiento en la ventana **Explorador de rendimiento**.  
  
7.  Opcional. Para añadir más archivos .dll, haga clic en **Destinos** y después seleccione **Agregar binario de destino**. Seleccione los archivos del cuadro de diálogo **Agregar binario de destino**.  
  
    > [!NOTE]
    >  No especifique el archivo ejecutable (.exe) que ejecuta los archivos DLL.  
  
## <a name="see-also"></a>Vea también  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)   
 [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)




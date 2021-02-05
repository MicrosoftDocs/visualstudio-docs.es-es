---
title: Limitar la instrumentación a archivos DLL específicos | Microsoft Docs
description: Aprenda a usar el método de generación de perfiles de instrumentación para limitar la recopilación de datos de generación de perfiles a uno o más archivos .dll en una aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7bd781f2c62a313a8e0c0b044103ca5da28021f8
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883376"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Procedimiento Limitar la instrumentación a archivos DLL específicos

El método de generación de perfiles de instrumentación permite limitar la recopilación de datos de generación de perfiles a uno o más archivos DLL en una aplicación. Para generar perfiles de uno o más archivos DLL en una aplicación, debe crearse una sesión de rendimiento que incluya los archivos .*dll* como destinos. Se pueden especificar los archivos DLL de los que se desea generar perfiles como proyectos de una solución de Visual Studio o como archivos binarios independientes.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Para limitar la instrumentación a archivos DLL específicos en una solución de Visual Studio

1. Abra la solución que contiene el archivo DLL en Visual Studio.

2. En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.

3. Elija **Instrumentación** como el método de generación de perfiles y después haga clic en **Siguiente**.

4. En **¿De cuál de los siguientes destinos disponibles desea generar perfiles?** , seleccione el nombre del proyecto .*dll* y después haga clic en **Siguiente**.

5. Haga clic en **Finalizar** para salir del asistente y mostrar la nueva sesión de rendimiento en la ventana **Explorador de rendimiento**.

6. Haga clic en **Destinos** y después seleccione **Agregar proyecto de destino**.

7. En la lista **Agregar proyecto de destino**, seleccione el proyecto ejecutable que desea utilizar para ejecutar el archivo DLL.

     Opcional. Puede agregar cualquier proyecto DLL del que desee generar perfiles.

8. Para evitar la recopilación de datos de un proyecto agregado, haga clic con el botón derecho en el nombre del proyecto y después desactive la casilla **Instrumento**.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Para especificar archivos DLL concretos para generar perfiles como binarios independientes

1. Abra Visual Studio.

2. En el menú **Analizar**, seleccione **Iniciar Asistente de rendimiento**.

3. En **¿De cuál de los siguientes destinos disponibles desea generar perfiles?** , seleccione **Generar perfiles de una biblioteca de vínculos dinámicos (.DLL)** y después haga clic en **Siguiente**.

4. En la segunda página del asistente, realice los siguientes pasos:

    - Escriba la ruta de acceso y el nombre del archivo .*dll* del que quiere generar perfiles en **ruta de acceso del archivo Dll**. También puede hacer clic en el botón de puntos suspensivos (...) para buscar el archivo en el cuadro de diálogo **Biblioteca de vínculos dinámicos de la que generar perfiles**. Tenga en cuenta que debe especificar la copia del archivo .*dll* que será iniciada por el archivo ejecutable (.*exe*) que seleccione a continuación.

    - Escriba la ruta de acceso y el nombre del archivo ejecutable (.*exe*) que ejecutará el archivo .*dll* en **Ruta ejecutable**. También puede hacer clic en el botón de puntos suspensivos (...) para buscar el archivo en el cuadro de diálogo **Ejecutable para iniciar**.

    - Opcional. Escriba los argumentos de línea de comandos que desea pasar al archivo ejecutable en **Argumentos de línea de comandos**. Si es necesario, especifique el directorio de trabajo de la aplicación en **Directorio de trabajo**.

    - Haga clic en **Siguiente**.

5. Elija **Instrumentación** como el método de generación de perfiles y después haga clic en **Siguiente**.

6. Haga clic en **Finalizar** para salir del asistente y mostrar la nueva sesión de rendimiento en la ventana **Explorador de rendimiento**.

7. Opcional. Para añadir más archivos .*dll*, haga clic en **Destinos** y después seleccione **Agregar binario de destino**. Seleccione los archivos del cuadro de diálogo **Agregar binario de destino**.

    > [!NOTE]
    > No especifique el archivo ejecutable (.*exe*) que ejecuta los archivos DLL.

## <a name="see-also"></a>Vea también

[Controlar la recopilación de datos](../profiling/controlling-data-collection.md)
[ Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)

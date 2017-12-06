---
title: "Depuración con Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: cb5128bf6412fa0f06c211f06f0d7f87353d52e0
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2017
---
# <a name="debugging-r-in-visual-studio"></a>Depuración de R en Visual Studio

Herramientas de R para Visual Studio (RTVS) se integra con la experiencia de depuración completa de Visual Studio (vea [Depuración en Visual Studio](../debugger/debugging-in-visual-studio.md). Esta compatibilidad incluye puntos de interrupción, adjuntar procesos de ejecución, inspeccionar y ver variables e inspeccionar la pila de llamadas. En este tema se exploran esos aspectos de la depuración que son únicos en R y RTVS.

El procedimiento para iniciar el depurador para el archivo de inicio de R en un proyecto de R es el mismo que para otros tipos de proyectos: use **Depurar > Iniciar depuración**, la tecla F5 o el comando **Archivo de inicio de origen** en la barra de herramientas de depuración: 

![Botón de inicio del depurador de R](media/debugger-start-button.png)

Para cambiar el archivo de inicio, haga clic con el botón derecho en un archivo en el Explorador de soluciones y seleccione **Establecer como script R de inicio**.

En todos los casos, al iniciar el depurador, se "obtiene" el archivo en la ventana interactiva, es decir, lo carga y lo ejecuta allí como se muestra en la salida de la ventana interactiva:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Tenga en cuenta que la función `rtvs::debug_source` se usa para obtener el script. Esta función es necesaria porque RTVS necesita modificar el código para preparar la depuración. Cuando se usa cualquier comando de obtención de RTVS y se adjunta un depurador, Visual Studio usa automáticamente `rtvs::debug_source`.

También puede adjuntar de forma manual el depurador desde la ventana interactiva directamente mediante el comando **Herramientas de R > Sesión > Adjuntar depurador**, el comando **Depurar > Adjuntar en R interactivo** o el comando **Adjuntar depurador** de la barra de herramientas de la ventana interactiva. Una vez que lo haya hecho, es su responsabilidad obtener los archivos que quiera depurar. Si quiere obtener manualmente los archivos, asegúrese de que usa `rtvs::debug_source` y no el comando `source` habitual en R.

Esta conexión entre el depurador y la ventana interactiva facilita acciones como llamar (y depurar) una función con diferentes valores de parámetro. Por ejemplo, supongamos que tiene la siguiente función en un archivo de origen (es decir, que se ha cargado en la sesión):

```R
add <- function(x, y) {
    return(x + y)
}
```

Después, establece un punto de interrupción en la instrucción `return`. Ahora, en la ventana interactiva, al escribir `add(4,5)` se detiene el depurador en su punto de interrupción.


## <a name="environment-browser-in-the-interactive-window"></a>Explorador de entorno en la ventana interactiva

Al estar detenido en el depurador, también está detenido en el aviso del explorador de entorno en la [ventana interactiva](interactive-repl.md). El aviso aparece como `Browse[n]>`, donde n es un número.

El Explorador de entorno admite una serie de comandos especiales:

| Comando | Descripción | 
| --- | --- |
| n | siguiente: ejecuta la siguiente instrucción en el archivo de código (igual que al depurar paso a paso por procedimientos). |
| s | depurar paso a paso por instrucciones: ejecuta la siguiente instrucción en el archivo de código, depurando paso a paso por instrucciones un ámbito de función si la siguiente instrucción es una llamada de función. | 
| f | finalizar: ejecuta el resto del ámbito de función actual y vuelve al autor de la llamada (igual que al salir de la depuración). |
| c, cont | continuar: ejecuta el programa hasta el siguiente punto de interrupción. | 
| C | salir: finaliza la sesión de depuración. |
| donde | mostrar pila: muestra la pila de llamadas en la ventana interactiva. |
| ayuda | mostrar ayuda: muestra los comandos disponibles en la ventana interactiva. |
| &lt;expr&gt; | evalúa la expresión en *expr*. |

![Explorador de entorno en la ventana interactiva](media/debugger-environment-browser.png)

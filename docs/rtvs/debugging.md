---
title: "Depuración con Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>Depuración de R en Visual Studio

Herramientas de R para Visual Studio (RTVS) se integra con la experiencia de depuración completa de Visual Studio (consulte [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md) [Depuración en Visual Studio]), incluidos los puntos de interrupción, adjuntar en procesos en ejecución, inspeccionar y observar variables, inspeccionar la pila de llamadas, etc. En este tema se exploran esos aspectos de la depuración que son únicos en R y RTVS.

Iniciar el depurador para el archivo de inicio de R en un proyecto de R es igual que para otros tipos de proyectos: use **Depurar > Iniciar depuración**, la tecla F5 o el comando **Source startup file** (Archivo de inicio de origen) en la barra de herramientas de depuración que se muestra a continuación. Para cambiar el archivo de inicio, haga clic con el botón derecho en un archivo en el Explorador de soluciones y seleccione **Establecer como script R de inicio**.

![Botón de inicio del depurador de R](media/debugger-start-button.png)

En todos los casos, al iniciar el depurador, se "obtiene" el archivo en la ventana interactiva, es decir, lo carga y lo ejecuta allí. De hecho, al iniciar la depuración, verá un resultado como el siguiente en la ventana interactiva:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Observará que estamos usando la función `rtvs::debug_source` para obtener el script. Esto es necesario porque RTVS necesita modificar el código para preparar la depuración. Si usa cualquiera de los comandos de RTVS (por ejemplo, al hacer clic con el botón derecho en un archivo en el Explorador de soluciones y ejecutar el comando **Archivos de origen seleccionados**), se redirigirá automáticamente la llamada a `rtvs::debug_source` si el depurador está adjuntado.

También puede adjuntar de forma manual el depurador desde la ventana interactiva directamente mediante el comando **Herramientas de R > Sesión > Adjuntar depurador**, el comando **Depurar > Adjuntar en R interactivo** o el comando **Adjuntar depurador** de la barra de herramientas de la ventana interactiva. Una vez que lo haya hecho, es su responsabilidad obtener los archivos que quiera depurar. Si quiere obtener los archivos de forma manual, asegúrese de que usa `rtvs::debug_source` y no el comando normal `source` de R. Es posible que esto funcione en _algunos_ casos, pero no podemos garantizar que la depuración funcione en todos los casos a menos que use el comando `rtvs::debug_source`.

Esta conexión entre el depurador y la ventana interactiva facilita acciones como llamar (y depurar) una función con diferentes valores de parámetro. Por ejemplo, supongamos que tiene una función similar a la siguiente en un archivo de origen (es decir, que se ha cargado en la sesión):

```R
add <- function(x, y) {
    return(x + y)
}
```

Después, establece un punto de interrupción en la instrucción `return`. Ahora, en la ventana interactiva, si escribe `add(4,5)`, verá que el depurador se detiene en el punto de interrupción.


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


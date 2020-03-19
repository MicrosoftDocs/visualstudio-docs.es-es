---
title: REPL interactivo para R
description: Describe cómo usar el entorno REPL interactivo para R en Studio, que está integrado en las ventanas del editor.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815001"
---
# <a name="work-with-the-r-interactive-window"></a>Trabajar con la ventana interactiva de R

Herramientas de R para Visual Studio (RTVS) proporciona la ventana R interactivo, también conocida como ventana **REPL** (read-eval-print loop), en la que se puede escribir código R y ver los resultados de inmediato. Todos los módulos, la sintaxis y las variables, además de IntelliSense, están disponibles en esta ventana.

La ventana R interactivo también se integra con las ventanas normales del editor de R. Puede seleccionar código y presionar **Ctrl**+**Entrar** o hacer clic con el botón derecho y seleccionar **Ejecutar en modo interactivo** para que el código se ejecute línea a línea en la ventana interactiva de R, como si lo hubiera escrito directamente. Cuando el cursor está en una sola línea en una ventana del editor, **Ctrl**+**Entrar** envía esa línea a la ventana interactiva de R y luego mueve el cursor a la línea siguiente. De este modo, solo tiene que presionar **Ctrl**+**Entrar** repetidamente para recorrer el código.

Para probar estas características, puede seguir el tutorial [Introducción a R](getting-started-with-r.md), así como las secciones de este artículo. Los [fragmentos de código](code-snippets-for-r.md) también funcionan en la ventana R interactivo como en las ventanas del editor de R.

## <a name="overview-of-the-interactive-window"></a>Información general sobre la ventana interactiva

Si escribe código R válido y presiona **Entrar** al final de la línea, se ejecuta el código en esa línea:

```repl
> 3 + 3
[1] 6
```

Al presionar **Entrar** en cualquier parte de una entrada de una sola línea, también se ejecuta esa línea.

Todas las entradas y salidas anteriores de REPL son de solo lectura y no se pueden cambiar. Pero se puede seleccionar y copiar texto de la ventana en cualquier momento, así como pegarlo. El código pegado se ejecuta como si se hubiera escrito línea a línea.

Es decir, al empezar a escribir una instrucción y presionar **Entrar**, RTVS sabe cuándo debe continuarse la instrucción y se pone en modo de varias líneas con un símbolo del sistema + a la izquierda y la sangría adecuada. RTVS también completa paréntesis, corchetes y llaves:

![Entrada de instrucción de varias líneas en la ventana R interactivo](media/repl-multiline-entry.png)

En este modo de varias líneas, la tecla **Entrar** ejecuta el bloque de código solo cuando está al final del bloque, de lo contrario inserta una nueva línea. Pero puede presionar **Ctrl**+**Entrar** en cualquier posición para ejecutar ese bloque de código de inmediato.

### <a name="toolbar-commands"></a>Comandos de la barra de herramientas

Aquí se muestra la ventana interactiva con su barra de herramientas:

![Ventana R interactivo con barra de herramientas](media/repl-window.png)

Los comandos de la barra de herramientas son los siguientes, la mayoría de los cuales tiene equivalentes de teclado y también están disponibles en los menús **Herramientas de R** > **Sesión** y **Herramientas de R** > **Directorio de trabajo** (o como se indica):

| Botón | Comando | Combinación de teclas | Description |
| --- | --- | --- | --- |
| ![Botón Restablecer](media/repl-toolbar-01-reset.png) | Reset | **Ctrl**+**Mayús**+**F10** | Restablece la sesión de la ventana R interactivo y borra todas las variables y el historial. |
| ![Botón Borrar](media/repl-toolbar-02-clear.png) | Clear | **Ctrl**+**L** | Borra la salida mostrada en la ventana R interactivo; no afecta a las variables de la sesión ni al historial. |
| ![Botones Historial](media/repl-toolbar-03-history.png) | Comando Historial anterior<br/>Comando Historial siguiente | **Arriba**, **Abajo**<br/>**Alt**+**Arriba**, **Alt**+**Abajo** | Se desplaza por el historial, con determinados comportamientos para los bloques de código de varias líneas. Vea [Historial](#history). |
| ![Botón Cargar área de trabajo](media/repl-toolbar-04-load-workspace.png) | Cargar área de trabajo | no disponible | Carga un área de trabajo guardada anteriormente (vea [Áreas de trabajo y sesiones](#workspaces-and-sessions)). |
| ![Botón Guardar área de trabajo como](media/repl-toolbar-05-save-workspace-as.png)| Guardar área de trabajo como | no disponible | Guarda el estado actual de la sesión como un área de trabajo (vea [Áreas de trabajo y sesiones](#workspaces-and-sessions)). |
| ![Botón Script de R de origen](media/repl-toolbar-06-source-r-script.png) | Script de R de origen | **Ctrl**+**Mayús**+**S** | Llama a `source` con el script de R activo en el editor de Visual Studio, que ejecuta el código.  Este botón solo aparece cuando hay un archivo de R abierto en el editor de Visual Studio. |
| ![Botón Script de R de origen con eco](media/repl-toolbar-07-source-r-script-with-echo.png) | Script de R de origen con eco | **Ctrl**+**Mayús**+**Entrar** | Es igual que Script de R de origen, pero muestra el contenido del script en la ventana R interactivo. |
| ![Botón Interrumpir R](media/repl-toolbar-08-interrupt-r.png)| Interrumpir R | **Esc** | Detiene cualquier código en ejecución en la ventana interactiva, como el bucle `while` de la captura de pantalla que se muestra al principio de esta sección. |
| ![Botón Asociar depurador](media/repl-toolbar-09b-attach-debugger.png)| Asociar depurador | no disponible | También disponible mediante el comando **Depurar** > **Attach to R Interactive** (Adjuntar en R interactivo). |
| ![Botón Establecer el directorio de trabajo en la ubicación del archivo de origen](media/repl-toolbar-10-set-working-directory-source.png)| Establecer el directorio de trabajo en la ubicación del archivo de origen | **Ctrl**+**Mayús**+**E** | Establece el directorio de trabajo en el archivo de origen que se ha cargado más recientemente en la ventana interactiva (mediante `source`). Vea [Directorio de trabajo](#working-directory). |
| ![Botón Establecer el directorio de trabajo en la ubicación del proyecto](media/repl-toolbar-11-set-working-directory-to-project.png) | Establecer el directorio de trabajo en la ubicación del proyecto | **Ctrl**+**Mayús**+**P** | Establece el directorio de trabajo en la raíz del proyecto cargado en Visual Studio. Vea [Directorio de trabajo](#working-directory). |
| (Campo de texto) | Seleccionar directorio de trabajo | no disponible | Campo de entrada directa para el directorio de trabajo. Vea [Directorio de trabajo](#working-directory). |

## <a name="workspaces-and-sessions"></a>Áreas de trabajo y sesiones

Al ejecutar código en la ventana interactiva se crea un contexto en la sesión actual. El contexto se compone de variables globales, definiciones de función, cargas de biblioteca y así sucesivamente. Este contexto se denomina colectivamente un *área de trabajo* y es posible guardar y cargar áreas de trabajo en cualquier momento.

Al hacer clic en el botón **Guardar área de trabajo como** o usar el comando **Herramientas de R** > **Sesión** > **Guardar área de trabajo como**, se pide una ubicación y un nombre de archivo (la extensión predeterminada es *.RData*).

Para guardar un área de trabajo con un nombre de archivo determinado (el predeterminado es *.RData*), haga clic en el botón **Guardar área de trabajo** en REPL:

Para volver a cargar un área de trabajo guardada previamente, haga clic en el botón **Cargar área de trabajo** o use **Herramientas de R** > **Sesión** > **Cargar área de trabajo** y vaya al archivo del área de trabajo.

El botón **Restablecer** o **Herramientas de R** > **Sesión** > **Restablecer** borra el contexto de la sesión. Si está usando una sesión remota, el restablecimiento también elimina el perfil de usuario en el equipo remoto para borrar todos los archivos almacenados allí. (Vea [Áreas de trabajo](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers)).

## <a name="working-directory"></a>Directorio de trabajo

Es habitual que los desarrolladores quieran cambiar su directorio de trabajo en una sesión interactiva. Varios comandos, disponibles en la barra de herramientas, el menú **Herramientas de R** > **Directorio de trabajo** y el menú contextual del proyecto, permiten establecer fácilmente un directorio de trabajo en la ubicación de un archivo de origen, la ubicación o el proyecto, o cualquier otra ubicación arbitraria. Esto ayuda a evitar la escritura de nombres de ruta de acceso completos o largos nombres de ruta de acceso relativos al hacer referencia a los archivos.

## <a name="history"></a>Historial

Cada línea que se escribe en la ventana R interactivo, incluso las líneas enviadas desde un editor, se conserva en el historial de REPL. Luego se puede navegar por historial con las teclas Arriba y Abajo como es probable que acostumbre a hacer en la línea de comandos.

Una diferencia es que, si empieza a escribir en la línea actual y presiona Arriba, esa línea actual se conserva en el historial aunque aún no la haya ejecutado.

El historial de la ventana R interactivo también funciona de forma inteligente con instrucciones de otro bloque de código que abarque líneas. Al recorrer el historial con las teclas Arriba y Abajo, los bloques de código de varias líneas se recuperan como una unidad completa y se muestran como la entrada actual. En este punto, las teclas de flecha se desplazan por ese bloque de código línea a línea, hasta que se llega a la parte superior o inferior. En la parte superior del bloque de código, la flecha Arriba recupera el elemento anterior del historial; en la línea inferior, la flecha Abajo recupera el elemento siguiente.

Este comportamiento facilita el caso típico de volver a ejecutar el último elemento del historial con una combinación de las teclas Flecha Arriba y **Entrar** y, a la vez, permite la edición de un bloque de código de varias líneas al presionar la tecla Flecha Arriba para navegar por él.

Para evitar el desplazamiento por bloques de código de varias líneas, use los botones de la barra de herramientas o **Alt**+**Arriba** y **Alt**-**Abajo**, y todos los bloques de este tipo se tratarán como una sola línea.

La manera más fácil de experimentar las características del historial es probarlas en la ventana interactiva. El código siguiente ofrece varias instrucciones adecuadas de una y varias líneas. En cambio, use la función copiar y pegar en cada instrucción individualmente para crear el historial adecuado. (También puede pegar el código en un archivo de código independiente y luego enviar las líneas a la ventana interactiva con **Ctrl**+**Entrar**).

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```
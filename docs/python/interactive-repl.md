---
title: Ventana interactiva de REPL de Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
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
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ca444dbe9fea25b205ae2060d462f23957368496
ms.lasthandoff: 04/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>Uso de la ventana interactiva de Python

Visual Studio proporciona una ventana interactiva read-evaluate-print loop (REPL) para cada entorno de Python, que ofrece mejoras con respecto al REPL obtenido con la línea de comandos `python.exe`. La ventana interactiva (que se abre con los comandos de menú **Ver > Otras ventanas > &lt;Entorno&gt; interactivo**) permite escribir código Python arbitrario y ver resultados inmediatos, que ayudan a aprender y experimentar con API, así como a desarrollar de forma interactiva código de trabajo para incluirlo en los proyectos.

![Ventana interactiva de Python](~/docs/python/media/interactive-window.png)

Visual Studio tiene una serie de modos de REPL de Python entre los que se puede elegir:

| REPL | Descripción | Editar | Depuración | Imágenes |
| --- | --- | --- | --- | --- |
| Estándar | REPL predeterminado, que habla directamente con Python | Edición estándar (multilínea, etc.) | Sí, mediante `$attach` | No |
| Depuración | REPL predeterminado, que habla directamente con el proceso de Python depurado | Edición estándar | Solo depuración | No |
| IPython | REPL habla con el back-end de IPython | Comandos de IPython, ventajas de PyLab | No | Sí, insertado en REPL |
| IPython sin PyLab | REPL habla con el back-end de IPython | IPython estándar | No | Sí, ventana independiente | 

En este tema se describen los modos de REPL **Estándar** y **Depurar**. Para obtener más información sobre los modos de IPython, vea [Using the IPython REPL](interactive-repl-ipython.md) (Uso de REPL de Python).

Para consultar una introducción a la ventana interactiva de Python, consulte el vídeo de youtube.com (2 minutos y 51 segundos) [Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introducción a Python en Visual Studio, parte 5: ventana interactiva de REPL).

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>Apertura de una ventana interactiva

Hay varias maneras de abrir la ventana interactiva de un entorno.

En primer lugar, cambie a la ventana Python Environments (Entornos de Python); para ello seleccione (**Ver > Otras ventanas > Entornos de Python** o presione Ctrl-K,Ctrl-`) y seleccione el comando o botón **Open Interactive Window** (Abrir ventana interactiva) de un entorno concreto.

![Vínculo a una ventana interactiva en la ventana Python Environments (Entornos de Python)](~/docs/python/media/interactive-window-opening.png)

En segundo lugar, en **Ver > Otras ventanas**, hay comandos de **Interactivo** para cada entorno, que suelen encontrarse cerca de la parte inferior del menú:

![Elementos de menú de la ventana interactiva en Ver > Otras ventanas](~/docs/python/media/interactive-window-menu.png)

En tercer lugar, puede abrir una ventana interactiva en el archivo de inicio del proyecto o en un archivo independiente; para ello, seleccione el comando de menú **Depurar > Ejecutar [Proyecto | Archivo] en la ventana interactiva de Python** (Mayús+Alt+F5):

![Menú Execute Project in Python Interactive (Ejecutar proyecto en la ventana interactiva de Python)](~/docs/python/media/interactive-execute-project.png)

Por último, puede seleccionar código en el archivo y usar el comando [send code to interactive command](#send-code-to-interactive-command) (enviar código a comando interactivo) descrito a continuación.

## <a name="interactive-window-options"></a>Opciones de la ventana interactiva

Puede controlar varios aspectos de la ventana interactiva a través de la opción **Configure interactive window** (Configurar ventana interactiva) en la ventana Python Environments (Entornos de Python) o a través de **Herramientas > Opciones > Herramientas de Python > Ventanas interactivas**:

![Opciones de la ventana interactiva de Python](media/interactive-window-options.png)

Tenga en cuenta que también hay un conjunto independiente de opciones para la **Ventana interactiva de depuración**, que controla el comportamiento durante una sesión de depuración:

![Opciones de depuración de la ventana interactiva de Python](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>Uso de la ventana interactiva

Cuando la ventana interactiva está abierta, puede empezar a escribir código línea por línea donde aparece el símbolo `>>>`. La ventana interactiva ejecuta cada línea según la escribe, lo que incluye importar módulos, definir variables, etc. Puede ver esto en las primeras dos líneas que aparecen en el gráfico siguiente:

![Ventana interactiva de Python](~/docs/python/media/interactive-window.png)

Se produce una excepción cuando una instrucción termina con dos puntos, como en el caso de la instrucción `for` anterior, porque la ventana interactiva sabe que necesita líneas de código adicionales para poder ejecutar correctamente el bloque de códigos. En este caso, el símbolo de la línea cambia a `...`, lo que indica que necesita escribir líneas adicionales para el bloque, tal como se muestra en las líneas cuarta y quinta del gráfico anterior. Si presiona Entrar en una línea en blanco, la ventana interactiva cierra el bloque y lo ejecuta en el intérprete.

> [!Tip]
> La ventana interactiva ofrece mejoras con respecto a la experiencia de REPL de línea de comandos de Python habitual, ya que aplica sangrías automáticamente a las instrucciones que pertenecen a un ámbito adyacente. Su historial (recuperado con la flecha arriba) también ofrece elementos multilínea, mientras que el REPL de la línea de comandos solo ofrece líneas simples.

La ventana interactiva resulta una forma magnífica de probar una biblioteca nueva. Puede importar la biblioteca, inspeccionar los subpaquetes, clases y funciones.  Python puede indicarle toda de esta información a través de la función `help()`.  Además, la compatibilidad de Python de Visual Studio proporciona sugerencias y documentación en función del modelo de código que se usa en el editor, lo que hace sin necesidad de ejecutar la biblioteca.  Cuando ejecuta código, Visual Studio usa información del tiempo de ejecución de Python para mejorar estas sugerencias.  

<a name="meta-commands"></a> La ventana interactiva también admite varios metacomandos. Todos los metacomandos empiezan con `$`, y puede escribir `$help` para obtener una lista de los metacomandos y `$help <command>` para obtener los detalles de uso de un comando específico.

| Metacomando | Descripción |
| --- | --- |
| `$$` | Inserta un comentario, lo que resulta útil para comentar el código a lo largo de la sesión. |
| `$attach` | Asocia el depurador de Visual Studio con el proceso de la ventana de REPL para habilitar la depuración. |
| `$cls`, `$clear` | Borra el contenido de la ventana del editor, pero deja intactos el historial y el contexto de ejecución. |
| `$help` | Muestra una lista de comandos o ayuda sobre un comando específico. |
| `$load` | Carga los comandos del archivo y los ejecuta hasta que terminan. |
| `$mod` | Cambia el ámbito actual al nombre del módulo especificado. |
| `$reset` | Restablece el entorno de ejecución al estado inicial, pero mantiene el historial. |
| `$wait` | Espera al menos el número de milisegundos especificado. |

Los comandos también son extensibles mediante MEF (Managed Extensibility Framework para. NET).

## <a name="switching-scopes"></a>Cambio de ámbitos

De forma predeterminada, la ventana interactiva de un proyecto se limita al archivo de inicio del proyecto, como si lo ejecutara desde el símbolo del sistema. Para un archivo independiente, se limita a dicho archivo. No obstante, el menú desplegable de la parte superior de la ventana interactiva permite cambiar en cualquier momento el ámbito durante la sesión de REPL:

![Ámbitos de la ventana interactiva](~/docs/python/media/interactive-scopes.png)

Después de importar un módulo, como escribir `import os`, verá opciones en el menú desplegable para cambiar a cualquier ámbito en dicho módulo. También verá un mensaje en la ventana interactiva que indica el nuevo ámbito, para que pueda realizar un seguimiento de cómo ha adoptado un estado determinado durante la sesión.

Al escribir `dir()` en un ámbito, se muestran identificadores válidos en dicho ámbito, como nombres de funciones, clases y variables. Por ejemplo, con `$mod importlib` seguido de `dir()`, se muestra lo siguiente:

![Ventana interactiva en el ámbito importlib](~/docs/python/media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>Comando Enviar código a Interactive

Además de trabajar directamente en la ventana interactiva, puede seleccionar código en el editor, hacer clic con el botón derecho y seleccionar **Enviar a Interactive**:

![Comando de menú Enviar a Interactive](~/docs/python/media/interactive-send-to.png)

Resulta útil para el desarrollo de código iterativo o evolutivo, incluido probar el código a medida que se desarrolla. Por ejemplo, después de enviar una porción de código a la ventana interactiva y ver la salida, puede presionar la flecha arriba para volver a ver el código, modificarlo y probarlo rápidamente si presiona las teclas Ctrl+Entrar. (Si presiona Entrar al final de la entrada, la ejecuta, pero, si presiona Entrar en el medio de la entrada, inserta una nueva línea). Cuando tenga el código que desea, puede volver a copiarlo con facilidad en el archivo del proyecto.

También puede seleccionar código, hacer clic con el botón derecho y seleccionar **Send to Defining Module** (Enviar al módulo de definición), lo que permite buscar el proceso interactivo para encontrar el módulo que coincide con el archivo actual que se va a editar. Si el comando encuentra el módulo correcto, usa el metacomando `$mod` para cambiar a dicho módulo (que forma parte del historial de sesiones de la ventana interactiva) y pega la selección en la ventana interactiva para evaluarla. Esto abrevia el proceso para copiar código en el editor, cambiar ámbitos en la ventana interactiva y pegar manualmente.

## <a name="intellisense-behavior"></a>Comportamiento de IntelliSense

La ventana interactiva incluye IntelliSense basándose en los objetos activos, a diferencia del editor de código, en el que IntelliSense se basa exclusivamente en el análisis de código fuente. Esto hace sugerencias más correctas en la ventana interactiva, sobre todo, con el código generado de forma dinámica. El inconveniente es que las funciones con efectos secundarios (como los mensajes de registro) pueden afectar a su experiencia de desarrollo.

Si plantea algún problema, cambie la configuración en **Herramientas > Opciones > Herramientas de Python > Ventanas interactivas** en el grupo **Modo de finalización**:

- **Never evaluate expressions** (Nunca evaluar expresiones): el motor de IntelliSense habitual se usará para las sugerencias.
- **Never evaluate expressions containing calls** (predeterminado) (Nunca evaluar expresiones que contienen llamadas): se evalúan las expresiones sencillas como `a.b`, pero las expresiones que contienen llamadas, como `a().b`, usan el motor habitual.
- **Always evaluate expressions** (Evaluar expresiones siempre): ejecuta la expresión completa para obtener sugerencias, con independencia de que tenga o no efectos secundarios.

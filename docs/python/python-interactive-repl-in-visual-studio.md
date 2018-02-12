---
title: Ventana interactiva de REPL de Python en Visual Studio | Microsoft Docs
description: "Cómo usar la ventana interactiva (REPL) para el código de Python en Visual Studio para el desarrollo rápido de código."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 78de05a74fd6626c6bd11e65e01b970c4bc8de34
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="working-with-the-python-interactive-window"></a>Uso de la ventana interactiva de Python

Visual Studio proporciona una ventana interactiva read-evaluate-print loop (REPL) para cada entorno de Python, que ofrece mejoras con respecto al REPL obtenido con la línea de comandos `python.exe`. La ventana interactiva (que se abre con los comandos de menú **Ver > Otras ventanas > &lt;entorno&gt; Interactivo**) le permite escribir código de Python arbitrario y ver resultados inmediatos. Esta manera de codificación le ayuda a obtener información y experimentar con las API y las bibliotecas, así como a desarrollar de manera interactiva código de trabajo para incluirlo en sus proyectos.

![Ventana interactiva de Python](media/interactive-window.png)

Visual Studio tiene una serie de modos de REPL de Python entre los que se puede elegir:

| REPL | Description | Editar | Depuración | Imágenes |
| --- | --- | --- | --- | --- |
| Estándar | REPL predeterminado, que habla directamente con Python | Edición estándar (multilínea, etc.). | Sí, mediante `$attach` | No |
| Depuración | REPL predeterminado, que habla directamente con el proceso de Python depurado | Edición estándar | Solo depuración | No |
| IPython | REPL habla con el back-end de IPython | Comandos de IPython, ventajas de PyLab | No | Sí, insertado en REPL |
| IPython sin PyLab | REPL habla con el back-end de IPython | IPython estándar | No | Sí, ventana independiente | 

En este tema se describen los modos de REPL **Estándar** y **Depurar**. Para obtener más información sobre los modos de IPython, vea [Using the IPython REPL](interactive-repl-ipython.md) (Uso de REPL de Python).

Para obtener un tutorial detallado con ejemplos, incluidas las interacciones con el editor como Ctrl+Entrar, vea [Paso 3: uso de la ventana interactiva de REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). Para ver un vídeo de introducción, eche un vistazo a [Python Interactive Window](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567) (Ventana interactiva de Python) de Microsoft Virtual Academy (2 minutos y 22 segundos).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567]

## <a name="opening-an-interactive-window"></a>Apertura de una ventana interactiva

Hay varias maneras de abrir la ventana interactiva de un entorno.

En primer lugar, cambie a la ventana Entornos de Python; para ello seleccione (**Ver > Otras ventanas > Entornos de Python** o presione Ctrl-K,Ctrl-`) y seleccione el comando o botón **Abrir ventana interactiva** de un entorno concreto.

![Vínculo a una ventana interactiva en la ventana Python Environments (Entornos de Python)](media/interactive-window-opening.png)

En segundo lugar, cerca del botón del menú **Ver > Otras ventanas**, se encuentra el comando **Ventana interactiva de Python**, que puede usar en su entorno predeterminado, así como un comando para cambiar a la ventana de entornos:

![Elementos de menú de la ventana interactiva en Ver > Otras ventanas](media/interactive-window-menu.png)

En tercer lugar, puede abrir una ventana interactiva en el archivo de inicio del proyecto o en un archivo independiente; para ello, seleccione el comando de menú **Depurar > Ejecutar [Proyecto | Archivo] en la ventana interactiva de Python** (Mayús+Alt+F5):

![Menú Execute Project in Python Interactive (Ejecutar proyecto en la ventana interactiva de Python)](media/interactive-execute-project.png)

Por último, puede seleccionar código en el archivo y usar el [comando Enviar código a Interactive](#send-code-to-interactive-command) descrito a continuación.

## <a name="interactive-window-options"></a>Opciones de la ventana interactiva

Puede controlar varios aspectos de la ventana interactiva mediante **Herramientas > Opciones > Herramientas de Python > Ventanas interactivas** (vea [Opciones](python-support-options-and-settings-in-visual-studio.md)):

![Opciones de la ventana interactiva de Python](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Uso de la ventana interactiva

Cuando la ventana interactiva está abierta, puede empezar a escribir código línea por línea donde aparece el símbolo `>>>`. La ventana interactiva ejecuta cada línea según la escribe, lo que incluye importar módulos, definir variables, entre otros:

![Ventana interactiva de Python](media/interactive-window.png)

La excepción se produce cuando se necesitan líneas de código adicionales para realizar una instrucción completa, como cuando una instrucción `for` termina en dos puntos como se ha mostrado anteriormente. En estos casos, el símbolo de la línea cambia a `...`, lo que indica que necesita escribir líneas adicionales para el bloque, tal como se muestra en las líneas cuarta y quinta del gráfico anterior. Si presiona Entrar en una línea en blanco, la ventana interactiva cierra el bloque y lo ejecuta en el intérprete.

> [!Tip]
> La ventana interactiva ofrece mejoras con respecto a la experiencia de REPL de línea de comandos de Python habitual, ya que aplica sangrías automáticamente a las instrucciones que pertenecen a un ámbito adyacente. Su historial (recuperado con la flecha arriba) también ofrece elementos multilínea, mientras que el REPL de la línea de comandos solo ofrece líneas simples.

<a name="meta-commands"></a> La ventana interactiva también admite varios metacomandos. Todos los metacomandos empiezan con `$`, y puede escribir `$help` para obtener una lista de los metacomandos y `$help <command>` para obtener los detalles de uso de un comando específico.

| Metacomando | Description |
| --- | --- |
| `$$` | Inserta un comentario, lo que resulta útil para comentar el código a lo largo de la sesión. |
| `$attach` | Asocia el depurador de Visual Studio con el proceso de la ventana de REPL para habilitar la depuración. |
| `$cls`, `$clear` | Borra el contenido de la ventana del editor, pero deja intactos el historial y el contexto de ejecución. |
| `$help` | Muestra una lista de comandos o ayuda sobre un comando específico. |
| `$load` | Carga los comandos del archivo y los ejecuta hasta que terminan. |
| `$mod` | Cambia el ámbito actual al nombre del módulo especificado. |
| `$reset` | Restablece el entorno de ejecución al estado inicial, pero mantiene el historial. |
| `$wait` | Espera al menos el número de milisegundos especificado. |

Los comandos también se extienden mediante extensiones de Visual Studio con la implementación y exportación de `IInteractiveWindowCommand` ([ejemplo](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switching-scopes"></a>Cambio de ámbitos

De forma predeterminada, la ventana interactiva de un proyecto se limita al archivo de inicio del proyecto, como si lo ejecutara desde el símbolo del sistema. Para un archivo independiente, se limita a dicho archivo. No obstante, el menú desplegable de la parte superior de la ventana interactiva permite cambiar en cualquier momento el ámbito durante la sesión de REPL:

![Ámbitos de la ventana interactiva](media/interactive-scopes.png)

Después de importar un módulo, como escribir `import importlib`, aparecen opciones en el menú desplegable para cambiar a cualquier ámbito en dicho módulo. Un mensaje en la ventana interactiva también indica el nuevo ámbito, para que pueda realizar un seguimiento de cómo ha adoptado un estado determinado durante la sesión.

Al escribir `dir()` en un ámbito, se muestran identificadores válidos en dicho ámbito, como nombres de funciones, clases y variables. Por ejemplo, con `import importlib` seguido de `dir()`, se muestra lo siguiente:

![Ventana interactiva en el ámbito importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Comando Enviar código a Interactive

Además de trabajar directamente en la ventana interactiva, puede seleccionar código en el editor, hacer clic con el botón derecho y seleccionar **Enviar a Interactive** presionar Ctrl+Entrar.

![Comando de menú Enviar a Interactive](media/interactive-send-to.png)

Este comando resulta útil para el desarrollo de código iterativo o evolutivo, incluido probar el código a medida que se desarrolla. Por ejemplo, después de enviar una porción de código a la ventana interactiva y ver la salida, puede presionar la flecha arriba para volver a ver el código, modificarlo y probarlo rápidamente si presiona las teclas Ctrl+Entrar. (Si presiona Entrar al final de la entrada, la ejecuta, pero, si presiona Entrar en el medio de la entrada, inserta una nueva línea). Cuando tenga el código que desea, puede volver a copiarlo con facilidad en el archivo del proyecto.

> [!Tip]
> De manera predeterminada, Visual Studio quita los mensajes de REPL >>> y ... al pegar código desde la ventana interactiva al editor. Puede cambiar este comportamiento en la pestaña **Herramientas > Opciones > Editor de texto > Python > Opciones avanzadas** con la opción **Quitar mensajes de REPL al pegar**. Vea [Opciones: Otras opciones](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

Al usar un archivo de código como un bloc de dictado, a menudo tiene un pequeño bloque de código que quiere enviar a la vez. Para agrupar el código, márquelo como una *celda de código*. Para ello, agregue un comentario que comience por `#%%` al principio de la celda, con lo cual se termina la anterior. Las celdas de código pueden contraerse y expandirse, y al usar Ctrl+Entrar dentro de una celda de código se envía la celda completa a la ventana interactiva y se pasa a la siguiente.

Visual Studio también detecta celdas de código que comienzan con comentarios como `# In[1]:`, que es el formato que se obtiene al exportar un Jupyter Notebook como un archivo de Python. Esta detección facilita la ejecución de un bloc de notas desde [Azure Notebooks](https://notebooks.azure.com/). Para ello, se descarga como un archivo de Python, se abre en Visual Studio y se usa Ctrl+Entrar para ejecutar cada celda.

![Celdas de código interactivas](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Comportamiento de IntelliSense

La ventana interactiva incluye IntelliSense basándose en los objetos activos, a diferencia del editor de código, en el que IntelliSense se basa exclusivamente en el análisis de código fuente. Estas sugerencias son más correctas en la ventana interactiva, sobre todo, con el código generado de forma dinámica. El inconveniente es que las funciones con efectos secundarios (como los mensajes de registro) pueden afectar a su experiencia de desarrollo.

Si este comportamiento es un problema, cambie la configuración en **Herramientas > Opciones > Herramientas de Python > Ventanas interactivas** en el grupo **Modo de finalización**, como se describe en [Opciones: Opciones de las ventanas interactivas](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).

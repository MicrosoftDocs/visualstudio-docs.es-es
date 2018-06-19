---
title: Opciones y configuración de Python
description: Referencia de las distintas configuraciones de Visual Studio que se relacionan con proyectos y código de Python.
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 23f78c754a9dc0f72e896128d857b70a49e8b09a
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032127"
---
# <a name="options-for-python-in-visual-studio"></a>Opciones de Python en Visual Studio

Para ver las opciones de Python, use el comando de menú **Herramientas > Opciones**, asegúrese de que la opción **Mostrar todas las configuraciones** está seleccionada y, después, vaya a **Herramientas de Python**:

![Cuadro de diálogo de opciones de Python, pestaña General](media/options-general.png)

También hay opciones adicionales específicas de Python en la pestaña **Editor de texto > Python > Opciones avanzadas** y en la pestaña **Entorno > Fuentes y colores** del grupo "Editor de texto".

> [!Note]
> El grupo **Experimental** contiene opciones de características que están aún en desarrollo y no se documentan aquí. A menudo, se habla de ellas en entradas del [blog de ingeniería de Python en Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="general-options"></a>Opciones generales

(Pestaña **Herramientas > Opciones > Python**).

| Opción | Default | Description |
| --- | --- | --- |
| Mostrar la Ventana de salida al crear entornos virtuales| Activado | Desactívela para evitar que aparezca la ventana de salida. |
| Mostrar la Ventana de salida al instalar o desinstalar paquetes | Activado | Desactívela para evitar que aparezca la ventana de salida. |
| Ejecutar siempre pip como administrador | Desactivado | Eleva siempre las operaciones `pip install` para todos los entornos. Al instalar paquetes, Visual Studio solicita privilegios de administrador si el entorno está situado en un área protegida del sistema de archivos como `c:\Program Files`. En ese mensaje, puede elegir elevar siempre `pip install` solo para ese entorno. Consulte la [pestaña de paquetes](python-environments-window-tab-reference.md#packages-tab). |
| Generar automáticamente la base de datos de finalización en el primer uso | Activado | *Se aplica a Visual Studio 2017, versión 15.5 y anteriores, y a versiones posteriores cuando se utiliza una base de datos de IntelliSense.* Prioriza la finalización de la base de datos de una biblioteca cuando escribe código que la usa. Para obtener más información, consulte [Referencia de pestañas de la ventana Entorno de Python - Pestaña IntelliSense](python-environments-window-tab-reference.md). |
| Omitir las variables PYTHONPATH de todo el sistema | Activado | PYTHONPATH se omite de manera predeterminada porque Visual Studio proporciona un medio más directo para especificar rutas de búsqueda en entornos y proyectos. Consulte [Rutas de acceso de búsqueda](search-paths.md) para más detalles. |
| Actualizar rutas de búsqueda al agregar archivos vinculados | Activado | Cuando se establece, agregar un [archivo vinculado](managing-python-projects-in-visual-studio.md#linked-files) a un proyecto actualiza las [rutas de búsqueda](search-paths.md) de manera que IntelliSense pueda incluir el contenido de la carpeta del archivo vinculado en su base de datos de finalización. Desactive esta opción para excluir dicho contenido de la base de datos de finalización. |
| Mostrar advertencia si no se encuentra el módulo importado | Activado | Desactive esta opción para suprimir las advertencias cuando sepa que un módulo importado no está disponible actualmente pero, de otro modo, no afecta a la operación de código. |
| Informar de sangría incoherente como | Advertencias | Como el intérprete de Python depende totalmente de la sangría adecuada para determinar el ámbito, Visual Studio genera advertencias de manera predeterminada cuando detecta sangrías incoherentes que pueden indicar errores de codificación. Se establece en *Errores* para ser incluso más estricto, lo que provoca que el programa se cierre en dichos casos. Para deshabilitar este comportamiento conjunto, seleccione *No*. |
| Buscar encuestas o noticias | Una vez a la semana | Establece la frecuencia con la que permite que Visual Studio pueda abrir una ventana que contiene una página web con elementos de noticias y encuestas relacionados con Python, si está disponible. Las opciones son *Nunca*, *Una vez al día*, *Una vez a la semana* y *Una vez al mes*. |
| Restablecer todos los cuadros de diálogo ocultos de forma permanente (botón) | N/D | Los diferentes cuadros de diálogo proporcionan opciones como **No volver a mostrar**. Use este botón para desactivar esas opciones y hacer que los cuadros de diálogo vuelvan a aparecer. |

![Cuadro de diálogo de opciones de Python, pestaña General](media/options-general.png)

## <a name="debugging-options"></a>Opciones de depuración

(Pestaña **Herramientas > Opciones > Python > Depuración**).

| Opción | Default | Description |
| --- | --- | --- |
| Preguntar antes de ejecutar si hay errores | Activado | Cuando se establece, le pide que confirme que quiere ejecutar código que contiene errores. Desactive esta opción para deshabilitar la advertencia. |
| Esperar a la entrada cuando el proceso termine de forma anómala<br/><br/>Esperar a la entrada cuando el proceso termine de manera correcta | Activado (para ambos) | Un programa de Python iniciado desde Visual Studio se ejecuta en su propia ventana de consola. De manera predeterminada, la ventana espera a que presione una tecla antes de cerrarla independientemente de cómo finaliza el programa. Para quitar ese mensaje y cerrar la ventana automáticamente, desactive una o ambas opciones. |
| Resultado del programa tee en la Ventana de salida de depuración | Activado | Muestra el resultado del programa en una ventana de consola independiente y en la ventana de salida de Visual Studio. Desactive esta opción para mostrar el resultado solo en la ventana de consola independiente. |
| Interrumpir en la excepción SystemExit con el código de salida de cero | Desactivado | Si se establece, detiene el depurador en esta excepción. Cuando se desactiva, el depurador se cierra sin interrupción. |
| Habilitar el depurado de la biblioteca estándar de Python | Desactivado | Hace posible la depuración paso a paso por instrucciones del código fuente de biblioteca estándar durante la depuración, pero aumenta el tiempo que tarda el depurador en comenzar.|

![Cuadro de diálogo de opciones de Python, pestaña Depuración](media/options-debugging.png)

## <a name="diagnostics-options"></a>Opciones de diagnóstico

(Pestaña **Herramientas > Opciones > Python > Diagnóstico**).

| Opción | Default | Description |
| --- | --- | --- |
| Incluye registros de análisis | Activado | Incluye registros detallados relacionados con el análisis de los entornos de Python instalados al guardar el diagnóstico en un archivo o copiarlo en el Portapapeles mediante los botones. Esta opción puede aumentar significativamente el tamaño del archivo generado, pero a menudo es necesaria para diagnosticar problemas de IntelliSense. |
| Guardar diagnóstico en archivo (botón) | N/D | Solicita un nombre de archivo y, a continuación, guarda el registro en un archivo de texto. |
| Copiar diagnóstico en Portapapeles (botón) | N/D | Coloca la totalidad del registro en el Portapapeles; esta operación puede tardar algún tiempo según el tamaño del registro. |

![Cuadro de diálogo Opciones de Python, pestaña Diagnóstico](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Opciones de las ventanas interactivas

(Pestaña **Herramientas > Opciones > Python > Ventanas interactivas**).

| Opción | Default | Description |
| --- | --- | --- |
| Scripts | N/D | Especifica una carpeta general para los scripts de inicio que se van a aplicar a las ventanas interactivas en todos los entornos. Vea [Scripts de inicio](python-environments-window-tab-reference.md#startup-scripts). En cambio, tenga en cuenta que esta característica no funciona actualmente. |
| Usar flechas arriba o abajo para navegar por el historial | Activado | Usa las teclas de flecha para navegar por el historial en la ventana interactiva. Desactive esta opción para usar las teclas de flecha para navegar dentro del resultado de la ventana interactiva en su lugar. |
| Modo de finalización | Solo se evalúan expresiones sin llamadas de función | El proceso de determinar los miembros disponibles en una expresión en la ventana interactiva puede necesitar la evaluación de la expresión actual sin terminar, lo que puede provocar efectos secundarios o funciones que se llaman varias veces. La opción predeterminada, *Solo evaluar las expresiones sin llamadas de función* excluye expresiones que aparecen para llamar a una función, pero evalúa otras expresiones. Por ejemplo, evalúa `a.b` pero no `a().b`.  *Nunca evaluar expresiones* evita los efectos secundarios usando solo el motor de IntelliSense normal para las sugerencias. *Evaluar todas las expresiones* evalúa la expresión completa para obtener sugerencias, independientemente de los efectos secundarios. |
| Ocultar sugerencias de análisis estático | Desactivado | Cuando se establece, muestra solo sugerencias que se obtienen evaluando la expresión. Si se combina con el modo de finalización *Nunca evaluar expresiones*, no aparecen finalizaciones útiles en la ventana interactiva. |

![Cuadro de diálogo de opciones de Python, pestaña Ventanas interactivas](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Opciones avanzadas del editor de Python

(Pestaña **Herramientas > Opciones > Editor de texto > Python > Opciones avanzadas**).

### <a name="completion-results"></a>Resultados de finalización

| Opción | Default | Description |
| --- | --- | --- |
| Mostrar la intersección de los miembros tras su finalización | Desactivado | Cuando se establece, muestra solo finalizaciones admitidas por todos los tipos posibles. |
| Filtrar la lista según una cadena de búsqueda | Activado | Aplica el filtrado de las sugerencias de finalización a medida que escribe (está activada de manera predeterminada). |
| Mostrar automáticamente finalizaciones para todos los identificadores | Activado | Desactive esta opción para deshabilitar las finalizaciones en las ventanas interactivas y en el editor. |

### <a name="selection-in-completion-list"></a>Selección en la lista de finalización

| Opción | Default | Description |
| --- | --- | --- |
| Confirmado escribiendo los siguientes caracteres | `{}[]().,:;+-*/%&&#124;^~=<>#@\` | Normalmente, estos caracteres siguen un identificador que puede seleccionarse de una lista de finalización, por lo que es conveniente confirmar la finalización simplemente escribiendo un carácter. Puede quitar o agregar caracteres específicos a la lista según se quiera.  |
| Entrar confirma la finalización actual | Activado | Cuando se establece, la tecla Entrar selecciona y aplica la finalización seleccionada actualmente como sucede con los caracteres anteriores (pero, por supuesto, no existe un carácter para Entrar por lo que no puede estar en esa lista directamente). |
| Agregar nueva línea al presionar Entrar al final de una palabra | Desactivado | De manera predeterminada, si escribe la palabra completa que aparece en el elemento emergente de finalización y presiona Entrar, confirma esa finalización. Al establecer esta opción, las finalizaciones se confirman de manera eficaz al dejar de escribir el identificador, de manera que Entrar inserta una línea nueva. |

### <a name="miscellaneous-options"></a>Otras opciones

| Opción | Default | Description |
| --- | --- | --- |
| Especificar el modo de esquematización al abrir los archivos | Activado | Activa automáticamente la característica de esquematización de Visual Studio en el editor al abrir un archivo de código de Python. |
| Quitar mensajes de REPL al pegar | Activado | Quita >>> y ... del texto pegado, lo que permite una transferencia sencilla de código de la ventana interactiva al editor. Desactive esta opción si necesita conservar esos caracteres al pegar desde otros orígenes. |
| Nombres de colores basados en tipos | Activado | Habilita los colores de la sintaxis en el código de Python. |

![Cuadro de diálogo Opciones del editor de Python, pestaña Opciones avanzadas](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Opciones de fuentes y colores

(Pestaña **Entorno > Fuentes y colores** dentro del grupo "Editor de texto").

Los nombres de las opciones de Pyhton están precedidas por "Python" y se explican por sí mismos. La fuente predeterminada para todos los temas de color de Visual Studio es Consolas de 10 pt, normal (no negrita). Los colores predeterminados varían según el tema. Normalmente, una fuente o un color se cambia si le resulta difícil de leer texto con la configuración predeterminada.

![Opciones de fuente y color de Python](media/options-fonts-and-colors.png)
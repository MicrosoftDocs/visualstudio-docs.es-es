---
title: Depuración en modo mixto para Python
description: Depuración simultánea de C++ y Python en Visual Studio, incluida la ejecución paso a paso entre entornos, la visualización de valores y la evaluación de expresiones.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a2848f04e2765c23f60de041e865e7684901b924
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962804"
---
# <a name="debug-python-and-c-together"></a>Depurar Python y C++ de forma conjunta

La mayoría de los depuradores normales de Python admiten la depuración de código de Python exclusivamente. En la práctica, sin embargo, Python se usa junto con C o C++ en escenarios que requieren alto rendimiento o la posibilidad de invocar directamente las API de plataforma. (Vea [Creación de una extensión de C++ para Python](working-with-c-cpp-python-in-visual-studio.md) para obtener un tutorial).

Visual Studio proporciona depuración en modo mixto simultánea e integrada para Python y C o C++ nativo. Para usar esta función, seleccione la opción **Herramientas de desarrollo nativo Python** para la carga de trabajo **Desarrollo de Python** en el instalador de Visual Studio.

> [!Note]
> La depuración en modo mixto no está disponible con Herramientas de Python para Visual Studio 1.x en Visual Studio 2015 y versiones anteriores.

Las características de depuración en modo mixto incluyen las siguientes opciones, tal y como se explica en este artículo:

- Pilas de llamadas combinada
- Transición entre código de Python y nativo
- Puntos de interrupción en ambos tipos de código
- Vea las representaciones de Python de objetos en marcos nativos y viceversa.
- Depuración en el ámbito de los proyectos de Python o C++

![Depuración en modo mixto para Python en Visual Studio](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | Para obtener una introducción a la compilación, las pruebas y la depuración de módulos de C nativos con Visual Studio, vea [Deep Dive: Create Native Modules](https://youtu.be/D9RlT06a1EI) (Profundización: Creación de módulos nativos) (youtube.com, 9 minutos 09 segundos). El vídeo se aplica a Visual Studio 2015 y 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Habilitación de la depuración en modo mixto en un proyecto de Python

1. Haga clic con el botón derecho en el proyecto de Python en el **Explorador de soluciones**, seleccione **Propiedades**, seleccione la pestaña **Depurar** y luego **Habilitar depuración de código nativo**. Esta opción habilita el modo mixto para todas las sesiones de depuración.

    ![Habilitación de la depuración de código nativo](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Cuando se habilita la depuración de código nativo, la ventana de resultados de Python podría desaparecer de inmediato al completarse el programa, sin ofrecer la pausa habitual **Presione cualquier tecla para continuar**. Para forzar una pausa, agregue la opción `-i` al campo **Ejecutar** > **Argumentos del intérprete** en la pestaña **Depurar** al habilitar la depuración de código nativo. Este argumento coloca al intérprete de Python en modo interactivo cuando finaliza el código, momento en que espera a que presione **Ctrl**+**Z** > **Entrar** para salir.

1. Al asociar el depurador en modo mixto a un proceso existente (**Depurar** > **Asociar al proceso**), use el botón **Seleccionar** para abrir el cuadro de diálogo **Seleccionar tipo de código**. A continuación, establezca la opción **Depurar estos tipos de código** y seleccione **Nativo** y **Python** en la lista:

    ![Selección de los tipos de código nativo y de Python](media/mixed-mode-debugging-code-type.png)

    La configuración del tipo de código es permanente, por lo que si quiere deshabilitar la depuración en modo mixto cuando asocie a otro proceso más adelante, borre el tipo de código **Python**.

    Es posible seleccionar otros tipos de código además de **Nativo**, o en lugar de este. Por ejemplo, si una aplicación administrada hospeda CPython, que, a su vez, usa módulos de extensión nativa, y desea depurar los tres, puede activar **Python**, **Nativo** y **Administrado** juntos para obtener una experiencia de depuración unificada que incluye pilas de llamadas combinadas y transición entre los tres tipos de tiempos de ejecución.

1. Al iniciar la depuración en modo mixto por primera vez, es posible que vea un cuadro de diálogo **Se necesitan símbolos de Python** (consulte [Símbolos para la depuración en modo mixto](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Debe instalar los símbolos solo una vez para cualquier entorno de Python. Los símbolos se incluyen automáticamente si instala la compatibilidad con Python mediante el instalador de Visual Studio (Visual Studio 2017 y versiones posteriores).

1. Para que el código fuente de Python estándar esté disponible durante la depuración, visite [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/), descargue el archivo correspondiente a la versión y extráigalo en una carpeta. Después, apunte Visual Studio a los archivos específicos de esa carpeta en el momento en el que se le pida.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Habilitación de la depuración en modo mixto en un proyecto de C o C++

Visual Studio (2017 versión 15.5 y posteriores) admite la depuración en modo mixto desde un proyecto de C o C++ (por ejemplo, al [insertar Python en otra aplicación, tal y como se describe en python.org](https://docs.python.org/3/extending/embedding.html)). Para habilitar la depuración en modo mixto, configure el proyecto de C o C++ para que inicie **Depuración nativa/Python**:

1. Haga clic con el botón derecho en el proyecto de C o C++ en el **Explorador de soluciones** y seleccione **Propiedades**.
1. Haga clic en la pestaña **Depuración**, **Depuración nativa/Python** en **Depurador para iniciar** y haga clic en **Aceptar**.

    ![Selección del depurador nativo o de Python en un proyecto de C o C++](media/mixed-mode-debugging-select-cpp-debugger.png)

Con este método, tenga en cuenta que no se puede depurar el propio iniciador *py.exe*, ya que genera un proceso secundario *python.exe* al que no se asocia el depurador. Si quiere iniciar *python.exe* directamente con argumentos, cambie la opción **Comando** de las propiedades de **Depuración nativa/Python** (se muestra en la imagen anterior) para especificar la ruta de acceso completa a *python.exe*. Luego especifique los argumentos en **Argumentos de comandos**.

### <a name="attaching-the-mixed-mode-debugger"></a>Asociación del depurador en modo mixto

En todas las versiones anteriores de Visual Studio, la depuración en modo mixto directa está habilitada solo al iniciar un proyecto de Python en Visual Studio, ya que los proyectos de C o C++ solo usan el depurador nativo. Sin embargo, puede asociar el depurador por separado:

1. Inicie el proyecto de C++ sin depurar (**Depurar** > **Iniciar sin depurar** o **Ctrl**+**F5**).
1. Seleccione **Depurar** > **Asociar al proceso**. En el cuadro de diálogo que aparece, seleccione el proceso adecuado y después use el botón **Seleccionar** para abrir el cuadro de diálogo **Seleccionar tipo de código**, donde puede seleccionar **Python**:

    ![Seleccionar Python como el tipo de depuración al asociar un depurador](media/mixed-mode-debugging-attach-type.png)

1. Seleccione **Aceptar** para cerrar ese cuadro de diálogo y, después, seleccione **Asociar** para iniciar el depurador.
1. Puede que necesite especificar una pausa adecuada o un retraso en la aplicación de C++ para garantizar que no llama al código de Python que quiere depurar antes de que pueda asociar el depurador.

## <a name="mixed-mode-specific-features"></a>Características específicas del modo mixto

- [Pilas de llamadas combinadas](#combined-call-stack)
- [Transición entre código de Python y nativo](#step-between-python-and-native-code)
- [Vista de valores PyObject en código nativo](#pyobject-values-view-in-native-code)
- [Vista de valores nativos en el código de Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Pila de llamadas combinada

La ventana **Pila de llamadas** muestra marcos de pila nativos y de Python intercalados, con marcas de transiciones entre los dos:

![Pila de llamadas combinadas con depuración en modo mixto](media/mixed-mode-debugging-call-stack.png)

Las transiciones aparecen como **[Código externo]**, sin especificar la dirección de la transición, siempre que la opción **Herramientas** > **Opciones** > **Depuración** > **General** > **Habilitar Solo mi código** esté establecida.

Al hacer doble clic en cualquier marco de llamada se vuelve activo y se abre el código fuente adecuado, si está disponible. Si el código fuente no está disponible, el marco sigue activo y se pueden inspeccionar las variables locales.

### <a name="step-between-python-and-native-code"></a>Transición entre código de Python y nativo

Cuando se usan los comandos **Depurar paso a paso por instrucciones** (**F11**) o **Paso a paso para salir** (**Mayús**+**F11**), el depurador en modo mixto controla correctamente los cambios entre tipos de código. Por ejemplo, cuando Python llama a un método de un tipo que está implementado en C, al depurar paso a paso por instrucciones en una llamada a ese método, se detiene al comienzo de la función nativa que implementa el método. Igualmente, cuando se llama a alguna función de API de Python mediante código nativo, se invoca código de Python. Por ejemplo, la depuración paso a paso por instrucciones de `PyObject_CallObject` en un valor de función que se definió originalmente en Python, se detiene al comienzo de la función de Python. También es posible pasar de código de Python a nativo para funciones nativas invocadas desde Python mediante [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Vista de valores PyObject en código nativo

Cuando está activo un marco nativo (C o C++), sus variables locales se muestran en la ventana **Variables locales** del depurador. En los módulos de extensión nativa de Python, muchas de estas variables son de tipo `PyObject` (que es una declaración typedef para `_object`), o algunos otros tipos de Python fundamentales (vea la lista siguiente). En la depuración en modo mixto, estos valores presentan un nodo secundario adicional con la etiqueta **[Vista de Python]**. Cuando se expande, este nodo muestra la representación de Python de la variable, idéntica a lo que vería si una variable local que hace referencia al mismo objeto estuviera presente en un marco de Python. Los elementos secundarios de este nodo son editables.

![Vista de Python en la ventana Expresiones locales](media/mixed-mode-debugging-python-view.png)

Para deshabilitar esta característica, haga clic con el botón derecho en cualquier parte de la ventana **Variables locales** y cambie la opción de menú **Python** > **Mostrar nodos de vista de Python**:

![Habilitación de la vista de Python en la ventana Expresiones locales](media/mixed-mode-debugging-enable-python-view.png)

Tipos de C que muestran nodos **[Vista de Python]** (si está habilitada esta característica):

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Vista de Python]** no aparece automáticamente para los tipos que crea el usuario. Al crear extensiones para Python 3.x, esto no suele ser un problema, ya que cualquier objeto tiene en última instancia un campo `ob_base` de uno de los tipos anteriores, lo que hace que aparezca **[Vista de Python]**.

Para Python 2.x, sin embargo, cada tipo de objeto declara normalmente su encabezado como una colección de campos insertados y no hay ninguna asociación entre los tipos personalizados creados y `PyObject` en el nivel de sistema de tipos en código de C o C++. Para habilitar los nodos **[Vista de Python]** para dichos tipos personalizados, edite el archivo *PythonDkm.natvis* en el [directorio de instalación de herramientas de Python](installing-python-support-in-visual-studio.md#install-locations) y agregue otro elemento en el código XML para el struct de C o la clase de C++.

Una opción alternativa (y mejor) es seguir [PEP 3123](https://www.python.org/dev/peps/pep-3123/) y usar un campo `PyObject ob_base;` explícito en lugar de `PyObject_HEAD`, si bien puede que esto no sea siempre posible por motivos de compatibilidad con versiones anteriores.

### <a name="native-values-view-in-python-code"></a>Vista de valores nativos en el código de Python

Al igual que en la sección anterior, puede habilitar una **[Vista de C++]** para valores nativos en la ventana **Variables locales** cuando un marco de Python está activo. Esta característica no está habilitada de forma predeterminada; para activarla, es necesario hacer clic con el botón derecho en la ventana **Variables locales** y cambiar la opción de menú **Python** > **Mostrar nodos de vista de C++**.

![Habilitación de la vista de C++ en la ventana Expresiones locales](media/mixed-mode-debugging-enable-cpp-view.png)

El nodo **[Vista de C++]** proporciona una representación de la estructura de C o C++ subyacente de un valor, idéntica a la que se vería en un marco nativo. Por ejemplo, muestra una instancia de `_longobject` (para el que `PyLongObject` es una declaración typedef) de un entero largo de Python, e intenta inferir tipos para clases nativas que haya creado usted mismo. Los elementos secundarios de este nodo son editables.

![Vista de C++ en la ventana Expresiones locales](media/mixed-mode-debugging-cpp-view.png)

Si un campo secundario de un objeto es de tipo `PyObject` o de uno de los otros tipos admitidos, tiene un nodo de representación **[Vista de Python]** (si esas representaciones están habilitadas), lo que hace que sea posible desplazarse por gráficos de objetos donde los vínculos no se exponen directamente a Python.

A diferencia de los nodos **[Vista de Python]**, que usan metadatos de objetos de Python para determinar el tipo del objeto, no hay ningún mecanismo similar confiable para **[Vista de C++]**. Por lo general, dado un valor de Python (es decir, una referencia `PyObject`), no es posible determinar con seguridad qué estructura de C o C++ lo respalda de manera confiable. El depurador en modo mixto intenta adivinar ese tipo examinando los distintos campos del tipo del objeto (como la referencia a `PyTypeObject` por su campo `ob_type`) que tienen tipos de puntero de función. Si uno de esos punteros de función hace referencia a una función que se puede resolver, y esa función tiene un parámetro `self` con un tipo más específico que `PyObject*`, se asume que ese tipo es el tipo de respaldo. Por ejemplo, si `ob_type->tp_init` de un objeto dado señala a la siguiente función:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

el depurador puede deducir correctamente que el tipo de C del objeto es `FobObject`. Si no puede determinar un tipo más preciso a partir de `tp_init`, continúa con los demás campos. Si no puede deducir el tipo a partir de ninguno de esos campos, el nodo **[Vista de C++]** presenta el objeto como una instancia de `PyObject`.

Para obtener siempre una representación útil de los tipos personalizados creados, es mejor registrar al menos una función especial cuando se registra el tipo y usar un parámetro `self` fuertemente tipado. Es obvio que la mayoría de los tipos cumplen este requisito; si no fuera así, `tp_init` es habitualmente la entrada más conveniente que se puede usar con esta finalidad. Una implementación ficticia de `tp_init` para un tipo que está presente exclusivamente para permitir la inferencia del tipo de depurador solo puede devolver cero inmediatamente, como en el ejemplo de código anterior.

## <a name="differences-from-standard-python-debugging"></a>Diferencias con la depuración estándar de Python

El depurador en modo mixto se diferencia del [depurador estándar de Python](debugging-python-in-visual-studio.md) en que presenta algunas características adicionales, pero carece de algunas funcionalidades relativas a Python:

- Características no admitidas: puntos de interrupción condicionales, ventana **Interactiva de depuración** y depuración remota entre plataformas.
- Ventana **Inmediato**: está disponible, pero con un subconjunto limitado de su funcionalidad, incluidas todas las limitaciones aquí indicadas.
- Versiones admitidas de Python: Solo CPython 2.7 y 3.3+.
- Visual Studio Shell: cuando se usa Python con Visual Studio Shell (por ejemplo, si se ha instalado con el instalador integrado), Visual Studio no puede abrir proyectos de C++ y la experiencia de edición de archivos de C++ es simplemente la de un editor de texto básico. Sin embargo, la depuración de C/C++ y la depuración en modo mixto se admiten completamente en Shell con código fuente, depuración paso a paso por instrucciones del código nativo y evaluación de expresiones de C++ en ventanas del depurador.
- Visualización y expansión de objetos: al visualizar objetos de Python en las ventanas de herramientas del depurador **Variables locales** e **Inspección**, el depurador en modo mixto muestra solo la estructura de los objetos. No evalúa automáticamente las propiedades ni muestra atributos calculados. Para colecciones, solo muestra elementos para tipos de colección integrados (`tuple`, `list`, `dict`, `set`). Los tipos de colección personalizados no se visualizan como colecciones, a menos que se hereden de algún tipo de colección integrado.
- Evaluación de expresiones: consulte a continuación.

### <a name="expression-evaluation"></a>Evaluación de expresiones

El depurador estándar de Python permite la evaluación de expresiones de Python arbitrarias en las ventanas **Inspección** e **Inmediato** cuando el proceso depurado se detiene en cualquier punto del código, siempre que no esté bloqueado en una operación de E/S u otra llamada del sistema similar. En la depuración en modo mixto, las expresiones arbitrarias pueden evaluarse solo cuando se detienen en el código de Python, después de un punto de interrupción o cuando depuran paso a paso por instrucciones el código. Las expresiones solo pueden evaluarse en el subproceso en el que se ha producido el punto de interrupción o la operación de depuración paso a paso por instrucciones.

Cuando se detiene en código nativo o en código Python donde las condiciones anteriores no se aplican (por ejemplo, después de una operación paso a paso para salir o en un subproceso diferente), la evaluación de expresiones se limita al acceso a las variables locales y globales en el ámbito del marco seleccionado actualmente, el acceso a sus campos y la indexación de los tipos de colección integrados con literales. Por ejemplo, la siguiente expresión se puede evaluar en cualquier contexto (siempre y cuando todos los identificadores hagan referencia a variables existentes y campos de los tipos adecuados):

```python
foo.bar[0].baz['key']
```

El depurador en modo mixto también resuelve tales expresiones de forma diferente. Todas las operaciones de acceso a miembros buscan solamente campos que son parte directamente del objeto (como una entrada en su `__dict__` o `__slots__`, o un campo de un struct nativo que se expone a Python mediante `tp_members`), y omite cualquier `__getattr__`, `__getattribute__` o lógica de descriptor. De igual forma, todas las operaciones de indexación omiten `__getitem__` y acceden directamente a la estructuras de datos internas de las colecciones.

Por motivos de coherencia, este esquema de resolución de nombres se usa con todas las expresiones que coincidan con las restricciones de la evaluación limitada de expresiones, con independencia de si se permiten expresiones arbitrarias en el punto de detención actual. Para forzar la semántica de Python apropiada cuando un evaluador completo está disponible, encierre la expresión entre paréntesis:

```python
(foo.bar[0].baz['key'])
```

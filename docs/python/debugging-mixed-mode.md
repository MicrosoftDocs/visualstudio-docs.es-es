---
title: "Depuración en modo mixto para Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 762829628e4f52c797bf98acf83a48eec0cbce6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-python-and-c-together"></a>Depuración conjunta de Python y C++

La mayoría de los depuradores normales de Python admiten la depuración de código de Python exclusivamente. Pero en la práctica, Python se usa junto con C o C++ cuando se requiere alto rendimiento o la posibilidad de invocar directamente las API de plataforma (vea [Creación de una extensión de C++ para Python](cpp-and-python.md) para obtener un ejemplo). Cuando se carga un proyecto de Python, Visual Studio proporciona depuración en modo mixto simultánea integrada para Python y código nativo C/C++, con pilas de llamadas combinadas, la posibilidad de moverse entre código de Python y nativo, puntos de interrupción en cualquier tipo de código y la posibilidad de ver representaciones de Python de objetos en marcos nativos y viceversa:

![Depuración en modo mixto](media/mixed-mode-debugging.png) 

Si quiere una introducción a la compilación, prueba y depuración de módulos de C nativos con Visual Studio, consulte el vídeo de youtube.com (9 minutos y 9 segundos) [Deep Dive: Creating Native Modules](https://youtu.be/D9RlT06a1EI) (Profundización: Creación de módulos nativos). El vídeo se aplica a Visual Studio 2015 y 2017.

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

> [!Note]
> La depuración en modo mixto no está disponible con Herramientas de Python para Visual Studio 1.x.

## <a name="enabling-mixed-mode-debugging"></a>Habilitación de la depuración en modo mixto

1. Haga clic con el botón derecho en el proyecto en el Explorador de soluciones, seleccione **Propiedades**, la pestaña **Depurar** y luego active la opción para **Habilitar depuración de código nativo**. Esta opción habilita el modo mixto para todas las sesiones de depuración.

    ![Habilitación de la depuración de código nativo](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]    
    > Cuando se habilita la depuración de código nativo, la ventana de salida de Python podría desaparecer de inmediato al completarse el programa, sin ofrecer la pausa habitual "Presione cualquier tecla para continuar…". Para forzar una pausa, agregue la opción `-i` al campo **Ejecutar > Argumentos del intérprete** en la pestaña **Depurar** al habilitar la depuración de código nativo. Este argumento colocará el intérprete de Python en modo interactivo cuando finalice el código, momento en que esperará a que presione Ctrl+Z, Entrar para salir.

1. Al asociar el depurador en modo mixto con un proceso existente (**Depurar > Asociar a proceso...**), elija el botón **Seleccionar...** para abrir el diálogo **Seleccionar tipo de código**, establezca la opción **Depurar estos tipos de código** y seleccione **Nativo** y **Python** en la lista:

    ![Selección de los tipos de código nativo y de Python](media/mixed-mode-debugging-code-type.png)

    La configuración del tipo de código es permanente, por lo que si quiere deshabilitar la depuración en modo mixto cuando se asocia a un proceso diferente más adelante, repita estos pasos y borre el tipo de código de Python.

    Es posible seleccionar otros tipos de código además de (o en lugar de) **Nativo**. Por ejemplo, si una aplicación administrada hospeda CPython, que, a su vez, usa módulos de extensión nativa, y desea depurar los tres, puede activar **Python**, **Nativo** y Administrado** juntos para obtener una experiencia de depuración unificada que incluye pilas de llamadas combinadas y transición entre los tres tipos de tiempos de ejecución.

1. Al iniciar la depuración en modo mixto por primera vez, es posible que vea un cuadro de diálogo **Se necesitan símbolos de Python**. Consulte [Símbolos de depuración en modo mixto](debugging-symbols-for-mixed-mode.md) para más información. Debe instalar los símbolos solo una vez para cualquier entorno de Python. Tenga en cuenta que si instala la compatibilidad de Python mediante el instalador de Visual Studio 2017, los símbolos se incluyen automáticamente.

1. También podría interesarle tener a mano el código fuente de Python. En el caso de Python estándar, el código fuente se obtiene en [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/). Descargue el archivo correspondiente a su versión y extráigalo en una carpeta. Después, apunte Visual Studio a los archivos específicos de esa carpeta en el momento en el que se le pida.

> [!Note]
> La depuración en modo mixto tal y como se describe aquí solo está habilitada cuando tiene un proyecto de Python cargado en Visual Studio. Ese proyecto determina el modo de depuración de Visual Studio, que es lo que hace que la opción de modo mixto esté disponible. En cambio, si tiene un proyecto de C++ cargado (como lo tendría al [insertar Python en otra aplicación como se describe en python.org](https://docs.python.org/3/extending/embedding.html), entonces Visual Studio usa el depurador nativo de C++ que no admite la depuración en modo mixto.
>
> En este caso, inicie el proyecto de C++ sin depurar (**Depurar > Iniciar sin depurar** o Ctrl+F5) y, después, use **Depurar > Asociar a proceso...**. En el cuadro de diálogo que aparece, seleccione el proceso adecuado, después use el botón **Seleccionar...** para abrir el cuadro de diálogo **Seleccionar tipo de código** en el que puede seleccionar Python como se muestra a continuación. Seleccione **Aceptar** para cerrar ese cuadro de diálogo y, después, seleccione **Asociar** para iniciar el depurador. Tenga en cuenta que puede que necesite especificar una pausa adecuada o un retraso en la aplicación de C++ para garantizar que no llama a la versión de Python que quiere depurar antes de que pueda asociar el depurador.
>
> ![Seleccionar Python como el tipo de depuración al asociar un depurador](media/mixed-mode-debugging-attach-type.png)

## <a name="mixed-mode-specific-features"></a>Características específicas del modo mixto

- [Pilas de llamadas combinadas](#combined-call-stack)
- [Transición entre código de Python y nativo](#stepping-between-python-and-native-code)
- [Vista de valores PyObject en código nativo](#pyobject-values-view-in-native-code)
- [Vista de valores nativos en el código de Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Pila de llamadas combinada

La ventana Pila de llamadas muestra marcos de pila nativos y de Python intercalados, con marcas de transiciones entre los dos:

![Pila de llamadas combinada](media/mixed-mode-debugging-call-stack.png)

> [!Note]
> Las transiciones aparecen como "[código externo]", sin especificar la dirección de la transición, si está establecida la opción **Herramientas > Opciones > Depuración > General > Habilitar Solo mi código**.

Al hacer doble clic en cualquier marco de llamada se vuelve activo y se abre el código fuente adecuado, si está disponible. Si el código fuente no está disponible, el marco sigue activo y se pueden inspeccionar las variables locales.

### <a name="stepping-between-python-and-native-code"></a>Transición entre código de Python y nativo

Cuando se usan los comandos Depurar paso a paso por instrucciones (F11) o Paso a paso para salir (Mayús+F11), del depurador en modo mixto controla correctamente los cambios entre tipos de código. Por ejemplo, cuando Python llama a un método de un tipo que está implementado en C, al depurar paso a paso por instrucciones en una llamada a ese método, se detiene al comienzo de la función nativa que implementa el método. Igualmente, cuando se llama a alguna función de API de Python mediante código nativo, se invoca código de Python. Por ejemplo, la depuración paso a paso por instrucciones de `PyObject_CallObject` en un valor de función que se definió originalmente en Python, se detiene al comienzo de la función de Python. También es posible pasar de código de Python a nativo para funciones nativas invocadas desde Python mediante [ctypes](http://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Vista de valores PyObject en código nativo

Cuando está activo un marco nativo (C o C++), sus variables locales se muestran en la ventana Variables locales del depurador. En los módulos de extensión nativa de Python, muchas de estas variables son de tipo `PyObject` (que es una declaración typedef para `_object`), o algunos otros tipos de Python fundamentales (vea la lista siguiente). En la depuración en modo mixto, estos valores presentan un nodo secundario adicional con la etiqueta "Vista de Python". Cuando se expande, este nodo muestra la representación de Python de la variable, idéntica a lo que vería si una variable local que hace referencia al mismo objeto estuviera presente en un marco de Python. Los elementos secundarios de este nodo son editables.

![Vista de Python](media/mixed-mode-debugging-python-view.png)

Para deshabilitar esta característica, haga clic con el botón derecho en cualquier parte de la ventana Variables locales y conmute la opción de menú **Python > Show Python View Nodes (Mostrar nodos de vista de Python)**:

![Habilitación de la vista de Python](media/mixed-mode-debugging-enable-python-view.png)

Tipos de C que muestran nodos "[Vista de Python]" (si está habilitada esta característica):

- `PyObject `
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

"[Vista de Python]" no aparece automáticamente para los tipos que crea usted mismo. Al crear extensiones para Python 3.x, esto no suele ser un problema porque cualquier objeto tiene en última instancia un campo `ob_base` de uno de los tipos anteriores, lo que hace que aparezca "[Vista de Python]". 

Para Python 2.x, sin embargo, cada tipo de objeto declara normalmente su encabezado como una colección de campos insertados y no hay ninguna asociación entre los tipos personalizados creados y `PyObject` en el nivel de sistema de tipos en código de C o C++. Para permitir los nodos "[Vista de Python]" para dichos tipos personalizados, edite `PythonDkm.natvis` en el [directorio de instalación de herramientas de Python](installation.md#install-locations) y agregue otro elemento en el XML para su struct de C o la clase de C++.

Una opción alternativa (y mejor) es seguir [PEP 3123](http://www.python.org/dev/peps/pep-3123/) y usar un campo `PyObject ob_base;` explícito en lugar de `PyObject_HEAD`, si bien puede que esto no sea siempre posible por motivos de compatibilidad con versiones anteriores.


### <a name="native-values-view-in-python-code"></a>Vista de valores nativos en el código de Python

Al igual que en la sección anterior, puede habilitar una "[Vista de C++]" para valores nativos en la ventana Variables locales cuando un marco de Python está activo. Esta característica no está habilitada de forma predeterminada; para activarla, es necesario hacer clic con el botón derecho en la ventana Variables locales y conmutar la opción de menú **Python > Show C++ View Nodes (Mostrar nodos de vista de C++)**.

![Habilitación de la vista de C++](media/mixed-mode-debugging-enable-cpp-view.png)

El nodo "[Vista de C++a]" proporciona una representación de la estructura de C o C++ subyacente de un valor, idéntica a la que vería en un marco nativo. Por ejemplo, muestra una instancia de `_longobject` (para el que `PyLongObject` es una declaración typedef) de un entero largo de Python, e intenta inferir tipos para clases nativas que haya creado usted mismo. Los elementos secundarios de este nodo son editables.

![Vista de C++](media/mixed-mode-debugging-cpp-view.png)

Si un campo secundario de un objeto es de tipo `PyObject` o de uno de los otros tipos admitidos, tiene un nodo de representación de "[Vista de Python]" (si esas representaciones están habilitadas), lo que hace que sea posible desplazarse por gráficos de objetos donde los vínculos no se exponen directamente a Python.

A diferencia de los nodos "[Vista de Python]", que usan metadatos de objetos de Python para determinar el tipo del objeto, no hay ningún mecanismo similar confiable para "[Vista de C++]". Por lo general, dado un valor de Python (es decir, una referencia `PyObject`), no es posible determinar con seguridad qué estructura de C o C++ lo respalda de manera confiable. El depurador en modo mixto intenta adivinar ese tipo examinando los distintos campos del tipo del objeto (como la referencia a `PyTypeObject` por su campo `ob_type`) que tienen tipos de puntero de función. Si uno de esos punteros de función hace referencia a una función que se puede resolver, y esa función tiene un parámetro `self` con un tipo más específico que `PyObject*`, se asume que ese tipo es el tipo de respaldo. Por ejemplo, si `ob_type->tp_init` de un objeto dado señala a la siguiente función:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

el depurador puede deducir correctamente que el tipo de C del objeto es `FobObject`. Si no puede determinar un tipo más preciso a partir de `tp_init`, continúa con los demás campos. Si no puede deducir el tipo a partir de ninguno de esos campos, el nodo "[Vista de C++]" presenta el objeto como una instancia de `PyObject`.

Para obtener siempre una representación útil de los tipos personalizados creados, es mejor registrar al menos una función especial cuando se registra el tipo y usar un parámetro `self` fuertemente tipado. Es obvio que la mayoría de los tipos cumplen este requisito; si no fuera así, `tp_init` es habitualmente la entrada más conveniente que se puede usar con esta finalidad. Una implementación ficticia de `tp_init` para un tipo que está presente exclusivamente para permitir la inferencia del tipo de depurador solo puede devolver cero inmediatamente, como en el ejemplo de código anterior.

## <a name="differences-from-standard-python-debugging"></a>Diferencias con la depuración estándar de Python

El depurador en modo mixto se diferencia del [depurador estándar de Python](debugging.md) en que presenta algunas características adicionales, pero carece de algunas funcionalidades relativas a Python:

- Características no admitidas: puntos de interrupción condicionales, ventana de depuración interactiva y depuración remota entre plataformas.
- Ventana Inmediato: está disponible pero con un subconjunto limitado de su funcionalidad, incluidas todas las limitaciones aquí indicadas.
- Admite versiones de Python: solo CPython 2.7 y 3.3 +.
- Visual Studio Shell: cuando se usa Python con Visual Studio Shell (por ejemplo, si se ha instalado con el instalador integrado), Visual Studio no puede abrir proyectos de C++ y la experiencia de edición de archivos de archivos de C++ es simplemente la de un editor de texto básico. Sin embargo, la depuración de C/C++ y la depuración en modo mixto se admiten completamente en Shell con código fuente, depuración paso a paso por instrucciones del código nativo y evaluación de expresiones de C++ en ventanas del depurador.
- Visualización y expansión de objetos: al visualizar objetos de Python en las ventanas Variables locales y Watch debugger tool (Inspeccionar herramienta de depurador), el depurador en modo mixto muestra la estructura de los objetos. No evalúa automáticamente las propiedades ni muestra atributos calculados. Para colecciones, solo muestra elementos para tipos de colección integrados (`tuple`, `list`, `dict`, `set`). Los tipos de colección personalizados no se visualizan como colecciones, a menos que se hereden de algún tipo de colección integrado.
- Evaluación de expresiones: consulte a continuación.

### <a name="expression-evaluation"></a>Evaluación de expresiones

El depurador estándar de Python permite la evaluación de expresiones de Python arbitrarias y ventanas Inmediato cuando el proceso de depuración se pausa en cualquier punto del código, siempre que no esté bloqueado en una operación de E/S u otra llamada del sistema similar. En la depuración en modo mixto, las expresiones arbitrarias pueden evaluarse solo cuando se detienen en el código de Python, después de un punto de interrupción o cuando depuran paso a paso por instrucciones el código. Las expresiones solo pueden evaluarse en el subproceso en el que se ha producido el punto de interrupción o la operación de depuración paso a paso por instrucciones.

Cuando se detiene en código nativo o en código Python donde las condiciones anteriores no se aplican (por ejemplo, después de una operación paso a paso para salir o en un subproceso diferente), la evaluación de expresiones se limita al acceso a las variables locales y globales en el ámbito del marco seleccionado actualmente, el acceso a sus campos y la indexación de los tipos de colección integrados con literales. Por ejemplo, la siguiente expresión se puede evaluar en cualquier contexto (siempre y cuando todos los identificadores hagan referencia a variables existentes y campos de los tipos adecuados):

```python
foo.bar[0].baz['key']
```

El depurador en modo mixto también resuelve tales expresiones de forma diferente. Todas las operaciones de acceso a miembros buscan solamente campos que son parte directamente del objeto (como una entrada en su `__dict__` o `__slots__`, o un campo de un struct nativo que se expone a Python mediante `tp_members`), y omite cualquier `__getattr__`, `__getattribute__` o lógica de descriptor. De igual forma, todas las operaciones de indexación omiten `__getitem__` y acceden directamente a la estructuras de datos internas de las colecciones.

Por motivos de coherencia, este esquema de resolución de nombres se usa con todas las expresiones que coincidan con las restricciones de la evaluación limitada de expresiones, con independencia de si se permiten expresiones arbitrarias en el punto de detención actual. Para forzar la semántica de Python apropiada cuando un evaluador completo está disponible, encierre la expresión entre paréntesis:

```python
(foo.bar[0].baz['key'])
```
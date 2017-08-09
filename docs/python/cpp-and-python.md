---
title: Trabajar con C++ y Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "Proceso y pasos para escribir una extensión o módulo de C++ para Python en Visual Studio"
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 6128d78b99b7fa82ffd5676678a49b1b6a0de177
ms.contentlocale: es-es
ms.lasthandoff: 07/18/2017

---

# <a name="creating-a-c-extension-for-python"></a>Creación de una extensión de C++ para Python

Los módulos escritos en C++ (o C) se suelen usar para ampliar las capacidades de un intérprete de Python y para permitir el acceso a funciones de bajo nivel del sistema operativo. Hay tres tipos principales de módulos:

- Módulos de acelerador: dado que Python es un lenguaje interpretado, algunas partes del código pueden escribirse en C++ para un mayor rendimiento. 
- Módulos de contenedor: los contenedores exponen las interfaces de C o C++ existentes a código de Python o exponen una API más propia de Python que se pueda usar fácilmente con este código.
- Módulos de acceso al sistema de bajo nivel: creados para tener acceso a características de bajo nivel del tiempo de ejecución de CPython, el sistema operativo o el hardware subyacente. 

Este tema le guía por la compilación de un módulo de extensión de C++ para CPython que calcula la tangente hiperbólica y la llama desde el código Python. Primero, se implementa la rutina en Python para demostrar la mejora del rendimiento de la implementación de la misma rutina en C++.

El enfoque adoptado aquí es el de las extensiones de CPython estándar que se describe en la [documentación de Python](https://docs.python.org/3/c-api/). Al final de este tema, en [Enfoques alternativos](#alternative-approaches), se describe una comparación entre este y otros medios.

## <a name="prerequisites"></a>Requisitos previos

Este tutorial se ha escrito para Visual Studio 2017 con las cargas de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo de Python** con sus opciones predeterminadas (como Python 3.6 como intérprete predeterminado). En la carga de trabajo **Desarrollo de Python**, active también la casilla de la derecha de **Herramientas de desarrollo nativo Python**, que establecerá la mayoría de las opciones descritas en este tema. (Esta opción también incluye la carga de trabajo de C++ automáticamente). 

![Selección de la opción Herramientas de desarrollo nativo Python](media/cpp-install-native.png)

Para obtener más información, vea [Installing Python Support for Visual Studio](installation.md) (Instalación de la compatibilidad de Python para Visual Studio), incluido el uso de otras versiones de Visual Studio. Si instala Python por separado, asegúrese de seleccionar **Download debugging symbols** (Descargar símbolos de depuración) y **Download debug binaries** (Descargar archivos binarios de depuración) en **Opciones avanzadas** en el programa de instalación. Esta opción le asegura que tendrá disponibles las bibliotecas de depuración necesarias si decide realizar una compilación de depuración.

> [!Note]
> Python también está disponible a través de la carga de trabajo **Aplicaciones analíticas y de ciencia de datos**, que incluye Anaconda 3 de 64 bits (con la versión más reciente de CPython) y la opción **Herramientas de desarrollo nativo de Python** predeterminada.

## <a name="create-the-python-application"></a>Crear la aplicación de Python

1. Cree un proyecto de Python en Visual Studio. Para ello, seleccione **Archivo > Nuevo > Proyecto**. Busque “Python”, seleccione la plantilla **Aplicación de Python**, dele un nombre, asígnele una ubicación y seleccione **Aceptar**.

1. En el archivo `.py` del proyecto, pegue el código siguiente, que realiza una prueba comparativa del cálculo de una tangente hiperbólica (implementada sin usar la biblioteca matemática para facilitar la comparación). No dude en escribir el código manualmente para experimentar algunas de las [características de edición de Python](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tanger function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()

        result = fn(DATA)

        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Ejecute el programa mediante **Depurar > Iniciar sin depurar** (Ctrl+F5) para ver los resultados. Cada prueba comparativa tarda unos segundos en completarse.

## <a name="create-the-core-c-project"></a>Crear el proyecto de C++ principal

1. Haga clic con el botón derecho en la solución en el Explorador de soluciones y seleccione **Agregar > Nuevo proyecto…**. Una solución de Visual Studio puede contener proyectos de Python y C++ juntos.

1. Busque "C++", seleccione **Proyecto vacío**, especifique un nombre (por ejemplo, TanhBenchmark) y seleccione **Aceptar**. Nota: Si ha instalado las **Herramientas de desarrollo nativo Python** con Visual Studio 2017, puede comenzar con la plantilla **Módulo de extensión de Python**, que incluye gran parte de lo que se describe aquí. En este tutorial partiremos de un proyecto vacío para mostrar la compilación del módulo de extensión paso a paso.

1. Cree un archivo de C++ en el nuevo proyecto. Para ello, haga clic con el botón derecho en el nodo **Archivos de código fuente**, seleccione **Agregar > Nuevo elemento…**, elija **Archivo de C++**, asígnele un nombre (como `module.cpp`) y seleccione **Aceptar**. Este paso es necesario para activar las páginas de propiedades de C++ en los pasos siguientes.

1. Haga clic con el botón derecho en el nuevo proyecto, seleccione **Propiedades** y, en la parte superior del cuadro de diálogo **Páginas de propiedades** que aparece, establezca **Configuración** en **Todas las configuraciones**.

1. Establezca las propiedades específicas como se describe a continuación y seleccione **Aplicar** (es posible que deba hacer clic fuera de un campo editable para que se habilite el botón **Aplicar**).

    | Tab | Propiedad | Valor | 
    | --- | --- | --- |
    | General | General > Nombre de destino | Establezca este campo de modo que coincida exactamente con el nombre del módulo tal como lo ve Python. |
    | | General > Extensión de destino | .pyd |
    | | Valores predeterminados del proyecto > Tipo de configuración | Biblioteca dinámica (.dll) |
    | C/C++ > General | Directorios de inclusión adicionales | Agregue la carpeta `include` de Python según sea necesario para la instalación, por ejemplo, `c:\Python36\include`. |     
    | C/C++ > Generación de código | Biblioteca en tiempo de ejecución | DLL multiproceso (/MD) (vea la advertencia siguiente) |
    | C/C++ > Preprocesador | Definiciones de preprocesador | Agregue `Py_LIMITED_API;` al inicio de la cadena. Esto restringe algunas de las funciones a las que se puede llamar desde Python y hace que el código sea más portátil entre versiones diferentes de Python. |
    | Enlazador > General | Directorios de bibliotecas adicionales | Agregue la carpeta `lib` de Python que contiene archivos `.lib` según sea necesario para la instalación, por ejemplo, `c:\Python36\libs`. (Asegúrese de apuntar a la carpeta `libs` que contiene archivos `.lib`, y *no* a la carpeta `Lib` que contiene archivos `.py`). | 

    > [!Tip]
    > Si no ve la pestaña C/C++, esto se debe a que el proyecto no contiene archivos identificados como archivos de código fuente de C/C++. Esta condición puede producirse si crea un archivo de código fuente sin una extensión `.c` o `.cpp`. Por ejemplo, si ha escrito accidentalmente `module.coo` en lugar de `module.cpp` en el anterior cuadro de diálogo Nuevo elemento, Visual Studio creará el archivo pero no establecerá el tipo de archivo en "Código C/C++", que es lo que activa la pestaña de propiedades de C/C++. Este error de identificación se mantiene incluso si cambia el nombre del archivo con `.cpp`. Para establecer el tipo de archivo correctamente, haga clic con el botón derecho en el archivo en el Explorador de soluciones, seleccione **Propiedades** y establezca **Tipo de archivo** en **Código C/C++**.

    > [!Warning]
    > No establezca la opción **C/C++ > Generación de código > Biblioteca en tiempo de ejecución** en "DLL de depuración multiproceso (/MDd)" ni siquiera para una configuración de depuración. Seleccione el tiempo de ejecución de "DLL multiproceso (/MD)", ya que es con lo que se compilan los binarios de Python que no son de depuración. Si por accidente establece la opción /MDd, verá el error *C1189: Py_LIMITED_API is incompatible with Py_DEBUG, Py_TRACE_REFS, and Py_REF_DEBUG* (C1189: Py_LIMITED_API no es compatible con Py_DEBUG, Py_TRACE_REFS y Py_REF_DEBUG) al compilar una configuración de depuración del archivo DLL. Además, si quita `Py_LIMITED_API` para evitar el error de compilación, Python se bloqueará al intentar importar el módulo. (El bloqueo se produce en la llamada del archivo DLL a `PyModule_Create`, como se describe más adelante, con el mensaje de salida *Fatal Python error: PyThreadState_Get: no current thread* [Error irrecuperable Python: PyThreadState_Get: ningún subproceso actual]).
    >
    > Tenga en cuenta que la opción /MDd es lo que se usa para compilar los binarios de depuración de Python (como python_d.exe), pero si se selecciona para un archivo DLL de extensión también se producirá el error de compilación con `Py_LIMITED_API`.
   
1. Haga clic con el botón derecho en el proyecto de C++ y seleccione **Compilar** para probar sus configuraciones (de depuración y de lanzamiento). Los archivos `.pyd` están en la carpeta *solución* en **Depuración** y **Lanzamiento**, no en la carpeta del proyecto de C++.

1. Agregue el código siguiente al archivo `.cpp` principal del proyecto de C++:

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh(x) {
        return sinh(x) / cosh(x);
    }
    ```

1. Compile el proyecto de C++ para confirmar que el código es correcto.


## <a name="convert-the-c-project-to-an-extension-for-python"></a>Convertir el proyecto de C++ a una extensión para Python

Para convertir el DLL de C++ en una extensión para Python, debe modificar el método exportado de modo que interactúe con tipos de Python. Después, debe agregar una función que exporte el módulo, junto con las definiciones de los métodos del módulo. Para obtener información general sobre lo que se muestra aquí, vea [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) (Manual de referencia de API de Python/C) y, en especial, [Module Objects](https://docs.python.org/3/c-api/module.html) (Objetos de módulo) en python.org. (No olvide seleccionar su versión de Python en el control desplegable situado en la esquina superior derecha).

1. En el archivo de C++, incluya `Python.h` en la parte superior:

    ```cpp
    include <Python.h>
    ```

1. Modifique el método `tanh` para aceptar y devolver tipos de Python:

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Agregue una estructura que defina la manera en que la función `tanh` de C++ se muestra en Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Agregue una estructura que defina el módulo como lo verá Python:

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Agregue un método al que Python llame cuando cargue el módulo, con el nombre `PyInit_<module-name>`, donde *&lt;module_name&gt;* debe coincidir exactamente con la propiedad **General > Nombre de destino** del proyecto de C++ (es decir, coincide con el nombre del archivo `.pyd` compilado por el proyecto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compile el archivo DLL otra vez para comprobar el código.

## <a name="test-the-code-and-compare-the-results"></a>Probar el código y comparar los resultados

Ahora que tiene el archivo DLL estructurado como una extensión de Python, puede hacer referencia a él desde el proyecto de Python, importar el módulo y usar sus métodos.

Hay dos maneras de hacer que el archivo DLL esté disponible para Python. En primer lugar, puede agregar una referencia desde el proyecto de Python al proyecto de C++, siempre y cuando se encuentren en la misma solución de Visual Studio:

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto de Python y seleccione **Referencias**. En el cuadro de diálogo, seleccione la pestaña **Proyectos**, el proyecto **superfastcode** y **Aceptar**.

En segundo lugar, puede instalar el módulo en el entorno global de Python, de modo que también esté disponible para otros proyectos de Python. Esto normalmente requiere que actualice la base de datos de finalizaciones de IntelliSense para ese entorno. También es necesario actualizar al quitar el módulo del entorno.

1. Si usa Visual Studio 2017, ejecute el instalador de Visual Studio, seleccione **Modificar**, seleccione **Componentes individuales > Compiladores, herramientas de compilación y entornos de ejecución > Conjunto de herramientas de Visual C++ 2015.3 v140**. Este paso es necesario porque que Python (para Windows) se compila con Visual Studio 2015 (versión 14.0) y espera que esas herramientas estén disponibles al compilar una extensión mediante el método descrito aquí.

1. Cree un archivo denominado `setup.py` en el proyecto de C++. Para ello, haga clic con el botón derecho en el proyecto, seleccione **Agregar > Nuevos elementos...*, busque "Python", seleccione **Archivo de Python**, asígnele el nombre setup.py y haga clic en **Aceptar**. Cuando el archivo aparezca en el editor, pegue el código siguiente en él:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    Vea [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (Compilar extensiones de C y C++) en python.org para consultar la documentación de este script.

1. El código `setup.py` le indica a Python que debe compilar la extensión (con el conjunto de herramientas de Visual Studio 2015 C++), lo que sucede en la línea de comandos. Abra un símbolo del sistema con privilegios elevados, vaya a la carpeta que contiene el proyecto de C++ (y `setup.py`) y escriba el comando siguiente:

    ```bash
    pip install .
    ```

Ahora puede llamar al código de `tanh` y comparar su rendimiento con la implementación de Python:

1. Agregue las líneas siguientes en `tanhbenchmark.py` para llamar al método `fast_tanh` exportado desde el archivo DLL y agréguelo a la salida de la prueba comparativa. Si escribe la instrucción `from s` manualmente, verá que `superfastcode` aparece en la lista de finalización y, después de escribir `import`, aparecerá el método `fast_tanh`.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Ejecute el programa de Python y verá que la rutina de C++ se ejecuta aproximadamente entre 15 y 20 veces más rápido que la implementación de Python.

## <a name="debug-the-c-code"></a>Depurar el código de C++

La [compatibilidad con Python en Visual Studio](installation.md) incluye la capacidad de [depurar código de Python y de C++ al mismo tiempo](debugging-mixed-mode.md). Para usar esta depuración en modo mixto, realice lo siguiente:

1. Haga clic con el botón derecho en el proyecto de Python en el Explorador de soluciones, seleccione **Propiedades**, elija la pestaña **Depurar** y, después, seleccione la opción **Depurar > Habilitar depuración de código nativo**.

    > [!Tip]
    > Cuando se habilita la depuración de código nativo, la ventana de salida de Python podría desaparecer de inmediato al completarse el programa, sin ofrecer la pausa habitual "Presione cualquier tecla para continuar…". Para forzar una pausa, agregue la opción `-i` al campo **Ejecutar > Argumentos del intérprete** en la pestaña **Depurar** al habilitar la depuración de código nativo. Este argumento colocará el intérprete de Python en modo interactivo cuando finalice el código, momento en que esperará a que presione Ctrl+Z, ENTRAR para salir. (Como alternativa, si no le importa modificar el código de Python, puede agregar las instrucciones `import os` y `os.system("pause")` al final del programa. Este código duplica la petición de pausa original).

1. En el código de C++, establezca un punto de interrupción en la primera línea del método `tanh` y, después, inicie el depurador. El depurador se detendrá cuando se realice la llamada al código:

    ![Detener en un punto de interrupción en el código de C++](media/cpp-debugging.png)

1. En este momento puede recorrer el código de C++, examinar variables, etc., como se detalla en [Debugging C++ and Python Together](debugging-mixed-mode.md) (Depurar C++ y Python juntos).

## <a name="alternative-approaches"></a>Enfoques alternativos 

Existen otros métodos para crear extensiones de Python, como se describe en la tabla siguiente. La primera entrada de CPython es lo que ya se ha tratado en este tema.

| Enfoque | Año | Usuarios representativos | Ventajas | Inconvenientes |
| --- | --- | --- | --- | --- |
| Módulos de extensión de C/C++ para CPython | 1991 | biblioteca estándar | [Amplia documentación y tutoriales](https://docs.python.org/3/c-api/). Control total. | Compilación, portabilidad, administración de referencias. Extensos conocimientos de C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generar enlaces para muchos lenguajes a la vez. | Sobrecarga excesiva si Python es el único destino. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Sin compilación, amplia disponibilidad. | El acceso y la mutación de estructuras de C son complicados y propensos a errores. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Semejante a Python. Muy maduro. Alto rendimiento. | Compilación, nueva sintaxis y cadena de herramientas. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilidad de integración, compatibilidad con PyPy. | Nuevo, menos maduro. |


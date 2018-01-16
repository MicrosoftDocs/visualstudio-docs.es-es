---
title: Trabajar con C++ y Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
description: "Proceso y pasos para escribir una extensión o módulo de C++ para Python en Visual Studio"
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: a1e5568f30177d3f4664d1cc1ebd7192539b86bf
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="creating-a-c-extension-for-python"></a>Creación de una extensión de C++ para Python

Los módulos escritos en C++ (o C) se suelen usar para ampliar las capacidades de un intérprete de Python y para permitir el acceso a funciones de bajo nivel del sistema operativo. Hay tres tipos principales de módulos:

- Módulos de acelerador: dado que Python es un lenguaje interpretado, algunas partes del código pueden escribirse en C++ para un mayor rendimiento. 
- Módulos de contenedor: los contenedores exponen las interfaces de C o C++ existentes a código de Python o exponen una API más propia de Python que se pueda usar fácilmente con este código.
- Módulos de acceso al sistema de bajo nivel: creados para tener acceso a características de bajo nivel del tiempo de ejecución de CPython, el sistema operativo o el hardware subyacente.

Este artículo le guía por la compilación de un módulo de extensión de C++ para CPython que calcula la tangente hiperbólica y realiza una llamada desde el código de Python. Primero, se implementa la rutina en Python para demostrar la mejora relativa del rendimiento de la implementación de la misma rutina en C++.

El enfoque adoptado aquí es el de las extensiones de CPython estándar que se describe en la [documentación de Python](https://docs.python.org/3/c-api/). Al final de este artículo, en [Enfoques alternativos](#alternative-approaches), se describe una comparación entre este y otros medios.

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio 2017 con las cargas de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo de Python** instaladas con opciones predeterminadas.
- En la carga de trabajo **Desarrollo de Python**, seleccione también el cuadro de la derecha de **Herramientas de desarrollo nativo de Python**. Esta opción establece la mayor parte de la configuración descrita en este artículo. (Esta opción también incluye la carga de trabajo de C++ automáticamente).

![Selección de la opción Herramientas de desarrollo nativo Python](media/cpp-install-native.png)

- La instalación de la carga de trabajo **Aplicaciones de ciencia de datos y de análisis** también incluye Python y la opción **Herramientas de desarrollo nativo Python** de forma predeterminada.

Para obtener más información, vea [Installing Python Support for Visual Studio](installation.md) (Instalación de la compatibilidad de Python para Visual Studio), incluido el uso de otras versiones de Visual Studio. Si instala Python por separado, asegúrese de seleccionar **Download debugging symbols** (Descargar símbolos de depuración) y **Download debug binaries** (Descargar archivos binarios de depuración) en **Opciones avanzadas** en el programa de instalación. Esta opción le asegura que tendrá disponibles las bibliotecas de depuración necesarias si decide realizar una compilación de depuración.

## <a name="create-the-python-application"></a>Crear la aplicación de Python

1. Cree un proyecto de Python en Visual Studio. Para ello, seleccione **Archivo > Nuevo > Proyecto**. Busque “Python”, seleccione la plantilla **Aplicación de Python**, dele un nombre, asígnele una ubicación y seleccione **Aceptar**.

1. En el archivo `.py` del proyecto, pegue el código siguiente, que realiza una prueba comparativa del cálculo de una tangente hiperbólica (implementada sin usar la biblioteca matemática para facilitar la comparación). No dude en escribir el código manualmente para experimentar algunas de las [características de edición de Python](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
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
        '''Applies the hyperbolic tangent function to map all values in
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
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Ejecute el programa mediante **Depurar > Iniciar sin depurar** (Ctrl + F5) para ver los resultados. Puede ajustar la variable `COUNT` para cambiar el tiempo que tardan en ejecutarse las pruebas comparativas. Para los fines de este tutorial, establezca el número para que cada prueba comparativa tarde aproximadamente dos segundos.

## <a name="create-the-core-c-project"></a>Crear el proyecto de C++ principal

1. Haga clic con el botón derecho en la solución en el Explorador de soluciones y seleccione **Agregar > Nuevo proyecto…**. Una solución de Visual Studio puede contener proyectos de Python y C++ juntos.

1. Busque "C++", seleccione **Proyecto vacío**, especifique un nombre (en este artículo, se usa "superfastcode") y seleccione **Aceptar**. Nota: Si ha instalado las **Herramientas de desarrollo nativo Python** con Visual Studio 2017, puede comenzar con la plantilla **Módulo de extensión de Python**, que incluye gran parte de lo que se describe aquí. En este tutorial partiremos de un proyecto vacío para mostrar la compilación del módulo de extensión paso a paso.

1. Cree un archivo de C++ en el nuevo proyecto. Para ello, haga clic con el botón derecho en el nodo **Archivos de código fuente**, seleccione **Agregar > Nuevo elemento…**, elija **Archivo de C++**, asígnele un nombre (como `module.cpp`) y seleccione **Aceptar**. Este paso es necesario para activar las páginas de propiedades de C++ en los pasos siguientes.

1. Haga clic con el botón derecho en el proyecto de C++ en Solución y seleccione **Propiedades**.

1. En la parte superior del cuadro de diálogo **Páginas de propiedades** que aparece, establezca **Configuración** como **Todas las configuraciones** y **Plataforma** como **Win32**.

1. Establezca las propiedades específicas tal y como se describe en la tabla siguiente y, luego, seleccione **Aceptar**.

    | Tab | Property | Valor |
    | --- | --- | --- |
    | General | General > Nombre de destino | Especifique el nombre del módulo tal y como quiera referirse a él desde Python en las instrucciones `from...import`. Use este mismo nombre en C++ al definir el módulo para Python. Si quiere utilizar el nombre del proyecto como nombre del módulo, deje el valor predeterminado `$(ProjectName)`. |
    | | General > Extensión de destino | .pyd |
    | | Valores predeterminados del proyecto > Tipo de configuración | Biblioteca dinámica (.dll) |
    | C/C++ > General | Directorios de inclusión adicionales | Agregue la carpeta `include` de Python según sea necesario para la instalación; por ejemplo, `c:\Python36\include`.  |
    | C/C++ > Preprocesador | Definiciones de preprocesador | Agregue `Py_LIMITED_API;` al principio de la cadena (incluido el punto y coma). Esta definición restringe algunas de las funciones a las que se puede llamar desde Python y hace que el código pueda moverse con mayor facilidad entre versiones diferentes de Python. |
    | C/C++ > Generación de código | Biblioteca en tiempo de ejecución | DLL multiproceso (/MD) (vea la advertencia siguiente) |
    | Enlazador > General | Directorios de bibliotecas adicionales | Agregue la carpeta `libs` de Python que contiene archivos `.lib` según sea necesario para la instalación, por ejemplo, `c:\Python36\libs`. (Asegúrese de apuntar a la carpeta `libs` que contiene archivos `.lib`, y *no* a la carpeta `Lib` que contiene archivos `.py`). |

    > [!Tip]
    > Si no ve la pestaña C/C++ en las propiedades del proyecto, esto se debe a que este no contiene archivos identificados como archivos de código fuente de C/C++. Esta condición puede producirse si crea un archivo de código fuente sin una extensión `.c` o `.cpp`. Por ejemplo, si ha escrito accidentalmente `module.coo` en lugar de `module.cpp` en el anterior cuadro de diálogo Nuevo elemento, Visual Studio creará el archivo pero no establecerá el tipo de archivo en "Código C/C++", que es lo que activa la pestaña de propiedades de C/C++. Este error de identificación se mantiene incluso si cambia el nombre del archivo con la extensión `.cpp`. Para establecer el tipo de archivo correctamente, haga clic con el botón derecho en el archivo en el Explorador de soluciones, seleccione **Propiedades** y establezca **Tipo de archivo** en **Código C/C++**.

    > [!Warning]
    > Establezca siempre la opción **C/C ++ > Generación de código > Biblioteca en tiempo de ejecución** como "DLL multiproceso (/MD)", incluso para una configuración de depuración, ya que esta es la configuración con la que se compilan los archivos binarios de Python. Si, por accidente, establece la opción "DLL de depuración multiproceso (/MDd)", al compilar una configuración de depuración, se producirá el error *C1189: Py_LIMITED_API no es compatible con Py_DEBUG, Py_TRACE_REFS ni Py_REF_DEBUG*. Además, si quita `Py_LIMITED_API` para evitar el error de compilación, Python se bloqueará al intentar importar el módulo. (El bloqueo se produce en la llamada del archivo DLL a `PyModule_Create`, como se describe más adelante, con el mensaje de salida *Fatal Python error: PyThreadState_Get: no current thread* [Error irrecuperable Python: PyThreadState_Get: ningún subproceso actual]).
    >
    > La opción /MDd se usa para compilar los binarios de depuración de Python (como python_d.exe), pero, si se selecciona para un archivo DLL de extensión, también se producirá el error de compilación con `Py_LIMITED_API`.

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

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Compile el proyecto de C++ para confirmar que el código es correcto.

## <a name="convert-the-c-project-to-an-extension-for-python"></a>Convertir el proyecto de C++ a una extensión para Python

Para convertir el DLL de C++ en una extensión para Python, debe modificar primero los métodos exportados de modo que interactúen con tipos de Python. Después, debe agregar una función que exporte el módulo, junto con las definiciones de los métodos del módulo. Para obtener información general sobre lo que se muestra aquí, vea [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) (Manual de referencia de API de Python/C) y, en especial, [Module Objects](https://docs.python.org/3/c-api/module.html) (Objetos de módulo) en python.org. (No olvide seleccionar su versión de Python en el control desplegable situado en la esquina superior derecha).

1. En el archivo de C++, incluya `Python.h` en la parte superior:

    ```cpp
    #include <Python.h>
    ```

    > [!Tip]
    > Si ve los errores *E1696: no se puede abrir el archivo de origen "Python.h"* o  *C1083: no se puede abrir el archivo de inclusión "Python.h": no existe tal archivo o directorio*, compruebe que ha establecido la configuración **C/C ++ > General > Directorios de inclusión adicionales** de las propiedades del proyecto en la carpeta `include` de la instalación de Python, tal y como se describe en el paso 6 de [Crear el proyecto de C++ principal](#create-the-core-c-project).

1. Modifique el método `tanh_impl` para aceptar y devolver tipos de Python (`PyOjbect*`).

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Agregue una estructura que defina la manera en que la función `tanh_impl` de C++ se muestra en Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Agregue una estructura que defina el módulo como quiere que se haga referencia a él en el código de Python, concretamente cuando se usa la instrucción `from...import` (hágalo coincidir con el valor de las propiedades del proyecto en **Propiedades de configuración > General > Nombre de destino**). En el ejemplo siguiente, el nombre de módulo "superfastcode" significa que puede usar `from superfastcode import fast_tanh` en Python, porque `fast_tanh` se define en `superfastcode_methods`. (Los nombres de archivo internos del proyecto de C++, como module.cpp, no tienen importancia).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Agregue un método al que Python llame cuando cargue el módulo, con el nombre `PyInit_<module-name>`, donde *&lt;module_name&gt;* debe coincidir exactamente con la propiedad **General > Nombre de destino** del proyecto de C++ (es decir, coincide con el nombre del archivo `.pyd` compilado por el proyecto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Establezca la configuración de destino en "Versión" y compile el proyecto de C++ de nuevo para comprobar el código. Si se producen errores, realice las siguientes comprobaciones:
    - No se puede encontrar Python.h: compruebe que la ruta de acceso de **C/C++ > General > Directorios de inclusión adicionales** de las propiedades del proyecto apunta a la carpeta `include` de instalación de Python.
    - No se pueden encontrar las bibliotecas de Python: compruebe que la ruta de acceso de **Enlazador > General > Directorios de bibliotecas adicionales** de las propiedades del proyecto apunta a la carpeta `libs` de instalación de Python.
    - Errores del enlazador relacionados con la arquitectura de destino: cambie la arquitectura del proyecto del destino de C++ para que coincida con la de la instalación de Python.

## <a name="test-the-code-and-compare-the-results"></a>Probar el código y comparar los resultados

Ahora que tiene el archivo DLL estructurado como una extensión de Python, puede hacer referencia a él desde el proyecto de Python, importar el módulo y usar sus métodos.

### <a name="make-the-dll-available-to-python"></a>Poner el archivo DLL a disposición de Python

Hay dos maneras de hacer que el archivo DLL esté disponible para Python.

El primer método funciona si el proyecto de Python y el de C++ se encuentran en la misma solución. Vaya al Explorador de soluciones, haga clic con el botón derecho en el nodo **Referencias** del proyecto de Python y, después, seleccione **Agregar referencia**. En el cuadro de diálogo que aparecerá, seleccione la ficha **Proyectos**, el proyecto **superfastcode** (o el nombre que esté usando) y **Aceptar**.

El método alternativo, que se describe en los pasos siguientes, instala el módulo en el entorno global de Python, lo que hace que esté disponible también para otros proyectos de Python. Normalmente, realizar esta acción requiere actualizar la base de datos de finalización de IntelliSense para ese entorno. También es necesario actualizar al quitar el módulo del entorno.

1. Si usa Visual Studio 2017, ejecute el instalador de Visual Studio, seleccione **Modificar**, seleccione **Componentes individuales > Compiladores, herramientas de compilación y entornos de ejecución > Conjunto de herramientas de Visual C++ 2015.3 v140**. Este paso es necesario porque que Python (para Windows) se compila con Visual Studio 2015 (versión 14.0) y espera que esas herramientas estén disponibles al compilar una extensión mediante el método descrito aquí (tenga en cuenta que puede que necesite instalar una versión de 32 bits de Python y establecer el DLL como Win32 y no como x64).

1. Cree un archivo denominado `setup.py` en el proyecto de C++ haciendo clic con el botón derecho en el proyecto y seleccionando **Agregar > Nuevo elemento**. Luego, seleccione "Archivo C++ (.cpp)", asigne el nombre `setup.py` al archivo y seleccione **Aceptar** (al nombrar el archivo con la extensión `.py`, Visual Studio lo reconoce como Python aunque use la plantilla de archivos de C++). Cuando el archivo aparezca en el editor, pegue el código siguiente en él:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Vea [Building C and C++ Extensions](https://docs.python.org/3/extending/building.html) (Compilación de extensiones de C y C++) en python.org para obtener la documentación de este script.

1. El código `setup.py` le indica a Python que debe compilar la extensión que usa el conjunto de herramientas de C++ de Visual Studio 2015 cuando se use desde la línea de comandos. Abra un símbolo del sistema con privilegios elevados, vaya a la carpeta que contiene el proyecto de C++ (es decir, la carpeta que contenga `setup.py`) y escriba el comando siguiente:

    ```command
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Llamar al archivo DLL desde Python

Después de haber completado cualquiera de los métodos anteriores, puede llamar a la función `fast_tanh` desde el código de Python y comparar su rendimiento con la implementación de Python:

1. Agregue las líneas siguientes en el archivo `.py` para llamar al método `fast_tanh` exportado desde el archivo DLL y mostrar el resultado.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Ejecute el programa de Python (**Depurar > Iniciar sin depurar** o Ctrl + F5) y observe que la rutina de C++ se ejecuta de cinco a veinte veces más rápido que la implementación de Python. Una vez más, intente aumentar la variable `COUNT` para que las diferencias sean más pronunciadas. Tenga en cuenta también que una compilación de depuración del módulo de C++ se ejecuta de forma más lenta que una compilación de depuración, ya que esta última está menos optimizada y contiene varias comprobaciones de errores. No dude en alternar entre dichas configuraciones para compararlas.

## <a name="debug-the-c-code"></a>Depurar el código de C++

Visual Studio admite la depuración de código Python y C++ de forma conjunta.

1. Haga clic con el botón derecho en el proyecto de Python en el Explorador de soluciones, seleccione **Propiedades**, elija la pestaña **Depurar** y, después, seleccione la opción **Depurar > Habilitar depuración de código nativo**.

    > [!Tip]
    > Cuando se habilita la depuración de código nativo, la ventana de salida de Python podría desaparecer de inmediato al completarse el programa, sin ofrecer la pausa habitual "Presione cualquier tecla para continuar…". Para forzar una pausa, agregue la opción `-i` al campo **Ejecutar > Argumentos del intérprete** en la pestaña **Depurar** al habilitar la depuración de código nativo. Este argumento colocará el intérprete de Python en modo interactivo cuando finalice el código, momento en que esperará a que presione Ctrl+Z, ENTRAR para salir. (Como alternativa, si no le importa modificar el código de Python, puede agregar las instrucciones `import os` y `os.system("pause")` al final del programa. Este código duplica la petición de pausa original).

1. Seleccione **Archivo > Guardar** para guardar los cambios de propiedad.

1. Establezca la configuración de compilación como "Depurar" en la barra de herramientas de Visual Studio.

    ![Establecer la configuración de compilación como Depurar](media/cpp-set-debug.png)

1. Puesto que el código normalmente tarda más tiempo en ejecutarse en el depurador, puede que le interese cambiar la variable `COUNT` del archivo `.py` a un valor que sea unas cinco veces más pequeño (por ejemplo, cambiarlo de `500000` a `100000`).

1. En el código de C++, establezca un punto de interrupción en la primera línea del método `tanh_impl` e inicie el depurador (F5 o **Depurar > Iniciar depuración**). El depurador se detendrá cuando se realice la llamada a ese código. Si no se alcanza el punto de interrupción, compruebe que la configuración esté establecida como Depurar y que haya guardado el proyecto (esto no se realiza automáticamente al iniciar al depurador).

    ![Detener en un punto de interrupción en el código de C++](media/cpp-debugging.png)

1. En este punto puede recorrer el código de C++, examinar las variables, etc. Estas características se detallan en [Depuración conjunta de Python y C++](debugging-mixed-mode.md).

## <a name="alternative-approaches"></a>Enfoques alternativos

Existen diversos métodos para crear extensiones de Python, como se describe en la tabla siguiente. La primera entrada de CPython es lo que se ha tratado ya en este tema.

| Enfoque | Año | Usuarios representativos | Ventajas | Inconvenientes |
| --- | --- | --- | --- | --- |
| Módulos de extensión de C/C++ para CPython | 1991 | biblioteca estándar | [Amplia documentación y tutoriales](https://docs.python.org/3/c-api/). Control total. | Compilación, portabilidad, administración de referencias. Extensos conocimientos de C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generar enlaces para muchos lenguajes a la vez. | Sobrecarga excesiva si Python es el único destino. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Sin compilación, amplia disponibilidad. | El acceso y la mutación de estructuras de C son complicados y propensos a errores. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Semejante a Python. Muy maduro. Alto rendimiento. | Compilación, nueva sintaxis y nueva cadena de herramientas. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilidad de integración, compatibilidad con PyPy. | Nuevo, menos maduro. |

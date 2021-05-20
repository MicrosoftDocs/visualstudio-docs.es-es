---
title: Escritura de extensiones de C++ para Python
description: Un tutorial para crear una extensión de C++ para Python mediante Visual Studio, CPython y PyBind11, incluida la depuración en modo mixto.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 866b588b8b46477b397cda92076780d1955cfa83
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848310"
---
# <a name="create-a-c-extension-for-python"></a>Creación de una extensión de C++ para Python

Los módulos escritos en C++ (o C) se suelen usar para ampliar las capacidades de un intérprete de Python y para permitir el acceso a funciones de bajo nivel del sistema operativo. Hay tres tipos principales de módulos:

- Módulos de acelerador: dado que Python es un lenguaje interpretado, algunas partes del código pueden escribirse en C++ para un mayor rendimiento.
- Módulos de contenedor: exponen las interfaces de C o C++ existentes a código de Python o exponen una API más propia de Python que se pueda usar fácilmente con este código.
- Módulos de acceso al sistema de bajo nivel: creados para tener acceso a características de bajo nivel del tiempo de ejecución de `CPython`, el sistema operativo o el hardware subyacente.

Este artículo le guía por la compilación de un módulo de extensión de C++ para `CPython` que calcula la tangente hiperbólica y realiza una llamada desde el código de Python. Primero, se implementa la rutina en Python para demostrar la mejora relativa del rendimiento de la implementación de la misma rutina en C++.

En este artículo también se muestran dos formas para que C++ esté disponible para Python:

- Las extensiones de `CPython` estándar se describen en la [documentación de Python](https://docs.python.org/3/c-api/).
- [PyBind11](https://github.com/pybind/pybind11), que es el recomendado para C++ 11 debido a su sencillez.

El ejemplo completo de este tutorial se puede encontrar en [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio 2017 o posterior con la carga de trabajo **Desarrollo de Python** instalada, incluidas las **herramientas de desarrollo nativo de Python**, que incluye la carga de trabajo de C++ y los conjuntos de herramientas necesarios para las extensiones nativas.

    ![Selección de la opción Herramientas de desarrollo nativo Python](media/cpp-install-native.png)

    > [!Tip]
    > La instalación de la carga de trabajo **Aplicaciones de ciencia de datos y de análisis** también incluye Python y la opción **Herramientas de desarrollo nativo Python** de forma predeterminada.

Para más información sobre las opciones de instalación, consulte [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md). Si instala Python por separado, asegúrese de seleccionar **Download debugging symbols** (Descargar símbolos de depuración) en **Opciones avanzadas** en el programa de instalación. Esta opción es necesaria para usar la depuración en modo mixto entre el código de Python y el código nativo.

## <a name="create-the-python-application"></a>Crear la aplicación de Python

1. Cree un proyecto de Python en Visual Studio. Para ello, seleccione **Archivo** > **Nuevo** > **Proyecto**. Busque "Python", seleccione la plantilla **Aplicación de Python**, asígnele un nombre y una ubicación y seleccione **Aceptar**.

1. En el archivo *.py* del proyecto, pegue el código siguiente (o escríbalo manualmente para experimentar algunas de las [características de edición de Python](editing-python-code-in-visual-studio.md)). Este código calcula una tangente hiperbólica sin usar la biblioteca matemática, y es lo que se acelerará con extensiones nativas.

    > [!Tip]
    > Escriba el código en Python puro antes de volver a escribir en C++. De este modo, puede comprobar más fácilmente que el código nativo es correcto.

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Ejecute el programa mediante **Depurar** > **Iniciar sin depurar** (**Ctrl**+**F5**) para ver los resultados. Puede ajustar la variable `COUNT` para cambiar el tiempo que tarda en ejecutarse la prueba comparativa. Para los fines de este tutorial, establezca el número para que la prueba comparativa tarde aproximadamente dos segundos.

> [!TIP]
> Al ejecutar pruebas comparativas, use siempre **Depurar** > **Iniciar sin depurar** para evitar la sobrecarga producida cuando se ejecuta código dentro del depurador de Visual Studio.

## <a name="create-the-core-c-projects"></a>Crear los proyectos principales de C++

Siga las instrucciones de esta sección para crear dos proyectos de C++ idénticos denominados "superfastcode" y "superfastcode2". Más adelante usará dos enfoques diferentes en cada proyecto para exponer el código de C++ para Python.

1. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**. Una solución de Visual Studio puede contener proyectos de Python y C++ juntos (que es una de las ventajas de utilizar Visual Studio para Python).

1. Busque "C++", seleccione **Proyecto vacío**, especifique el nombre "superfastcode" ("superfastcode2" para el segundo proyecto) y seleccione **Aceptar**.

    > [!Tip]
    > Con las **herramientas de desarrollo nativo de Python** instaladas en Visual Studio, puede comenzar con la plantilla **Módulo de extensión de Python**, que incluye gran parte de lo que se describe a continuación. En este tutorial partiremos de un proyecto vacío para mostrar la compilación del módulo de extensión paso a paso. Una vez que comprenda el proceso, la plantilla le permite ahorrar tiempo al escribir sus propias extensiones.

1. Cree un archivo de C++ en el nuevo proyecto. Para ello, haga clic con el botón derecho en el nodo **Archivos de código fuente**, seleccione **Agregar** > **Nuevo elemento**, seleccione **Archivo de C++**, asígnele el nombre `module.cpp` y seleccione **Aceptar**.

    > [!Important]
    > Para activar las páginas de propiedades de C++ en los pasos siguientes, es necesario un archivo con la extensión *.cpp*.

1. Si usa un entorno de ejecución de Python de 64 bits, active la configuración **x64** mediante el menú desplegable de la barra de herramientas principal. Para un entorno de ejecución de Python de 32 bits, active la configuración de **Win32**.

1. Haga clic con el botón derecho en el proyecto de C++ en el **Explorador de soluciones** y seleccione **Propiedades**. El valor de **Configuración** debe ser **Activo (depurar)** y **Plataforma** será **Activo (x64)** o **Activo (Win32)** según la selección del paso anterior.

    > [!Tip]
    > Para sus propios proyectos, querrá configurar las configuraciones Debug y Release. Aquí solo se ajusta la configuración Debug y se establece para usar una compilación de *versión* de `CPython`, que deshabilita algunas características de depuración del entorno de ejecución de C++, incluidas las aserciones. El uso de archivos binarios de *depuración* de `CPython` (`python_d.exe`) requerirá diferentes ajustes.

1. Establezca las propiedades específicas tal y como se describe en la tabla siguiente y, luego, seleccione **Aceptar**.
    ::: moniker range=">=vs-2019"
    | Pestaña | Propiedad | Valor |
    | --- | --- | --- |
    | **General** | **General** > **Nombre de destino** | Especifique el nombre del módulo tal y como quiera referirse a él desde Python en las instrucciones `from...import`. Use este mismo nombre en C++ al definir el módulo para Python. Si quiere utilizar el nombre del proyecto como nombre del módulo, deje el valor predeterminado de **$(ProjectName)**. |
    | | **Opciones avanzadas** > **Extensión de archivo de destino** | **.pyd** |
    | | **Valores predeterminados del proyecto** > **Tipo de configuración** | **Biblioteca dinámica (.dll)** |
    | **C/C++** > **General** | **Directorios de inclusión adicionales** | Agregue la carpeta *include* de Python según sea necesario para la instalación; por ejemplo, `c:\Python36\include`.  |
    | **C/C++** > **Preprocesador** | **Definiciones de preprocesador** | **Solo CPython**: agregue `Py_LIMITED_API;` al principio de la cadena (incluido el punto y coma). Esta definición restringe algunas de las funciones a las que se puede llamar desde Python y hace que el código pueda moverse con mayor facilidad entre versiones diferentes de Python. Si usa PyBind11, no agregue esta definición, ya que causará errores de compilación. |
    | **C/C++** > **Generación de código** | **Biblioteca en tiempo de ejecución** | **DLL multiproceso (/MD)** (vea la advertencia siguiente) |
    | **Enlazador** > **General** | **Directorios de bibliotecas adicionales** | Agregue la carpeta *libs* de Python que contiene archivos *.lib* según sea necesario para la instalación, por ejemplo, `c:\Python36\libs`. (Asegúrese de apuntar a la carpeta *libs* que contiene archivos *.lib*, y *no* a la carpeta *Lib* que contiene archivos *.py*). |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | Pestaña | Propiedad | Valor |
    | --- | --- | --- |
    | **General** | **General** > **Nombre de destino** | Especifique el nombre del módulo tal y como quiera referirse a él desde Python en las instrucciones `from...import`. Use este mismo nombre en C++ al definir el módulo para Python. Si quiere utilizar el nombre del proyecto como nombre del módulo, deje el valor predeterminado de **$(ProjectName)**. Para `python_d.exe`, agregue `_d` al final del nombre. |
    | | **General** > **Extensión de destino** | **.pyd** |
    | | **Valores predeterminados del proyecto** > **Tipo de configuración** | **Biblioteca dinámica (.dll)** |
    | **C/C++** > **General** | **Directorios de inclusión adicionales** | Agregue la carpeta *include* de Python según sea necesario para la instalación; por ejemplo, `c:\Python36\include`.  |
    | **C/C++** > **Preprocesador** | **Definiciones de preprocesador** | Si está presente, cambie el valor **_DEBUG** a **NDEBUG** para que coincida con la versión que no es de depuración de `CPython`. (Al usar `python_d.exe`, deje esta opción sin cambios). |
    | **C/C++** > **Generación de código** | **Biblioteca en tiempo de ejecución** | **DLL multiproceso (/MD)** para que coincida con la versión que no es de depuración de `CPython`. (Al usar `python_d.exe`, deje esta opción sin cambios). |
    | **Enlazador** > **General** | **Directorios de bibliotecas adicionales** | Agregue la carpeta *libs* de Python que contiene archivos *.lib* según sea necesario para la instalación, por ejemplo, `c:\Python36\libs`. (Asegúrese de apuntar a la carpeta *libs* que contiene archivos *.lib*, y *no* a la carpeta *Lib* que contiene archivos *.py*). |
    ::: moniker-end
    
    > [!Tip]
    > Si no ve la pestaña C/C++ en las propiedades del proyecto, esto se debe a que este no contiene archivos identificados como archivos de código fuente de C/C++. Esta condición puede producirse si crea un archivo de código fuente sin una extensión *.c* o *.cpp*. Por ejemplo, si ha escrito accidentalmente `module.coo` en lugar de `module.cpp` en el anterior cuadro de diálogo Nuevo elemento, Visual Studio creará el archivo pero no establecerá el tipo de archivo en "Código C/C++", que es lo que activa la pestaña de propiedades de C/C++. Este error de identificación se mantiene incluso si cambia el nombre del archivo con la extensión `.cpp`. Para establecer el tipo de archivo correctamente, haga clic con el botón derecho en el archivo en el **Explorador de soluciones**, seleccione **Propiedades** y establezca **Tipo de archivo** en **Código C/C++** .

1. Haga clic con el botón derecho en el proyecto de C++ y seleccione **Compilar** para probar sus configuraciones (de **Depuración** y de **Lanzamiento**). Los archivos *.pyd* están en la carpeta **solución** en **Depuración** y **Lanzamiento**, no en la carpeta del proyecto de C++.

1. Agregue el código siguiente al archivo *module.cpp* del proyecto de C++:

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

1. Si aún no lo ha hecho, repita los pasos anteriores para crear un segundo proyecto denominado "superfastcode2" con contenido idéntico.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertir los proyectos de C++ en extensiones para Python

Para convertir el DLL de C++ en una extensión para Python, debe modificar primero los métodos exportados de modo que interactúen con tipos de Python. Después, debe agregar una función que exporte el módulo, junto con las definiciones de los métodos del módulo.

En las secciones siguientes se explica cómo realizar estos pasos con las extensiones de `CPython` y PyBind11.

### <a name="cpython-extensions"></a>Extensiones de CPython

Para obtener información sobre lo que se muestra en esta sección, consulte el [Manual de referencia de la API de Python/C](https://docs.python.org/3/c-api/index.html) y especialmente [Objetos de módulo](https://docs.python.org/3/c-api/module.html) en python.org (recuerde que debe seleccionar la versión de Python en el control desplegable de la esquina superior derecha para ver la documentación correcta).

1. En la parte superior de *module.cpp*, incluya *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Modifique el método `tanh_impl` para aceptar y devolver tipos de Python (`PyObject*`).

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Agregue una estructura que defina la manera en que la función `tanh_impl` de C++ se muestra en Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Agregue una estructura que defina el módulo como quiere que se haga referencia a él en el código de Python, concretamente cuando se usa la instrucción `from...import`. (Hágalo coincidir con el valor de las propiedades del proyecto en **Propiedades de configuración** > **General** > **Nombre de destino**). En el ejemplo siguiente, el nombre de módulo "superfastcode" significa que puede usar `from superfastcode import fast_tanh` en Python, porque se define `fast_tanh` en `superfastcode_methods`. (Los nombres de archivo internos del proyecto de C++, como *module.cpp*, no tienen importancia).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Agregue un método al que Python llame cuando cargue el módulo, con el nombre `PyInit_<module-name>`, donde &lt;module_name&gt; debe coincidir exactamente con la propiedad **General** > **Nombre de destino** del proyecto de C++ (es decir, coincide con el nombre del archivo de *.pyd* compilado por el proyecto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compile de nuevo el proyecto de C++ para verificar el código. Si se producen errores, vea la sección [Solución de problemas](#troubleshooting) a continuación.

### <a name="pybind11"></a>PyBind11

Si ha completado los pasos descritos en la sección anterior, sin duda ha observado que usa una gran cantidad de código reutilizable para crear las estructuras de módulo necesarias para el código de C++. PyBind11 simplifica el proceso a través de macros en un archivo de encabezado de C++ que consigue el mismo resultado con mucho menos código. Para obtener información sobre lo que se muestra en esta sección, consulte [PyBind11 basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (Fundamentos de PyBind11, en github.com).

1. Instale PyBind11 mediante pip: `pip install pybind11` o `py -m pip install pybind11`. (Como alternativa, puede instalar mediante la ventana Entornos de Python y, a continuación, usar su comando "Abrir en PowerShell" para el paso siguiente).

1. En el mismo terminal, ejecute `python -m pybind11 --includes` o `py -m pybind11 --includes`. Esto imprimirá una lista de rutas de acceso que debe agregar a la propiedad **C/C++**  > **General** > **Directorios de inclusión adicionales** (quitando el prefijo `-I`, si estuviera).

1. En la parte superior de un archivo *module.cpp* nuevo, que no incluye ninguno de los cambios de la sección anterior, incluya *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. En la parte inferior de *module.cpp*, use la macro `PYBIND11_MODULE` para definir el punto de entrada a la función de C++:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Compile el proyecto de C++ para verificar el código. Si se producen errores, vea la sección Solución de problemas a continuación.

### <a name="troubleshooting"></a>Solución de problemas

El módulo de C++ puede producir un error al compilar por las razones siguientes:

- No se puede localizar *Python.h* (**E1696: no se puede abrir el archivo de origen "Python.h"** o **C1083: no se puede abrir el archivo de inclusión "Python.h": no existe tal archivo o directorio**): verifique que la ruta de acceso en **C/C ++** > **General** > **Directorios de inclusión adicionales** de las propiedades del proyecto apunta a la carpeta *include* de la instalación de Python. Consulte el paso 6 en [Crear el proyecto de C++ principal](#create-the-core-c-projects).

- No se pueden encontrar las bibliotecas de Python: compruebe que la ruta de acceso de **Enlazador** > **General** > **Directorios de bibliotecas adicionales** de las propiedades del proyecto apunta a la carpeta *libs* de instalación de Python. Consulte el paso 6 en [Crear el proyecto de C++ principal](#create-the-core-c-projects).

- Errores del enlazador relacionados con la arquitectura de destino: cambie la arquitectura del proyecto del destino de C++ para que coincida con la de la instalación de Python. Por ejemplo, si el destino es **Win32** con el proyecto de C++, pero la instalación de Python es de 64 bits, cambie el proyecto de C++ a **x64**.

## <a name="test-the-code-and-compare-the-results"></a>Probar el código y comparar los resultados

Ahora que tiene los archivos DLL estructurados como extensiones de Python, puede hacerles referencia desde el proyecto de Python, importar los módulos y usar sus métodos.

### <a name="make-the-dll-available-to-python"></a>Poner el archivo DLL a disposición de Python

Hay dos maneras de hacer que el archivo DLL esté disponible para Python.

El primer método funciona si el proyecto de Python y el de C++ se encuentran en la misma solución. Vaya al **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Referencias** del proyecto de Python y, después, seleccione **Agregar referencia**. En el cuadro de diálogo que aparecerá, seleccione la pestaña **Proyectos**, los proyectos **superfastcode** y **superfastcode2** y **Aceptar**.

![Agregar una referencia al proyecto superfastcode](media/cpp-add-reference.png)

El método alternativo, descrito en los pasos siguientes, instala el módulo en el entorno de Python, lo que lo hace disponible también para otros proyectos de Python. Visite el [proyecto **setuptools**](https://setuptools.readthedocs.io/) para obtener documentación más completa.

1. Cree un archivo denominado *setup.py* en el proyecto de C++; para ello, haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **Nuevo elemento**. Luego, seleccione **Archivo C++ (.cpp)**, asigne el nombre `setup.py` al archivo y seleccione **Aceptar** (al nombrar el archivo con la extensión *.py*, Visual Studio lo reconoce como Python aunque use la plantilla de archivos de C++). Cuando aparezca el archivo en el editor, pegue el código siguiente en él tal y como sea adecuado para el método de extensión:

    Extensiones de **`CPython` (proyecto superfastcode):**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11` (proyecto superfastcode2):**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. Cree un segundo archivo denominado *pyproject.toml* en el proyecto de C++ y pegue el código siguiente en él.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Para compilar la extensión, haga clic con el botón derecho en la pestaña para abrir *pyproject.toml* y seleccione "Copiar ruta de acceso completa" (eliminaremos el nombre *pyproject.toml* de la ruta de acceso antes de usarlo).

1. En Explorador de soluciones, haga clic con el botón derecho en el entorno de Python activo y seleccione *Administrar paquetes de Python*.

    > [!Tip]
    > Si ya ha instalado el paquete, verá que aparece aquí. Haga clic en la "X" para desinstalarlo antes de continuar.

1. Pegue la ruta de acceso copiada en el cuadro de búsqueda y elimine `pyproject.toml` del final. A continuación, presione Entrar para instalar desde ese directorio.

    > [!Tip]
    > Si se produce un error en la instalación debido a un error de permiso, agregue `--user` e inténtelo de nuevo.


### <a name="call-the-dll-from-python"></a>Llamar al archivo DLL desde Python

Una vez que el archivo DLL está disponible para Python como se ha descrito en la sección anterior, ahora puede llamar a las funciones `superfastcode.fast_tanh` y `superfastcode2.fast_tanh2` del código de Python y comparar su rendimiento con la implementación de Python:

1. Agregue las líneas siguientes en el archivo *.py* para llamar a los métodos exportados desde los archivos DLL y mostrar los resultados.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Ejecute el programa de Python (**Depurar** > **Iniciar sin depurar** o **Ctrl**+**F5**) y observe que las rutinas de C++ se ejecutan aproximadamente de cinco a veinte veces más rápido que la implementación de Python. El resultado típico se muestra de la manera siguiente:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Si el comando **Iniciar sin depurar** está deshabilitado, haga clic con el botón derecho en el proyecto de Python en el **Explorador de soluciones** y seleccione **Establecer como proyecto de inicio**.

1. Intente aumentar la variable `COUNT` para que las diferencias sean más pronunciadas. Una compilación de **depuración** del módulo de C++ también se ejecuta de forma más lenta que una compilación de **lanzamiento**, ya que la compilación de **depuración** está menos optimizada y contiene varias comprobaciones de errores. No dude en cambiar entre esas configuraciones para ver la comparación (pero recuerde volver y actualizar las propiedades de antes para la configuración **Release**).

En la salida, puede ver que la extensión de PyBind11 no es tan rápida como la extensión de `CPython`, aunque sigue siendo mucho más rápida que la implementación pura de Python. Esta diferencia se debe en gran medida a que hemos usado la llamada `METH_O`, que no admite varios parámetros, nombres de parámetros o argumentos de palabras clave. PyBind11 genera código ligeramente más complejo para proporcionar una interfaz más de tipo Python a los autores de la llamada, pero como el código de prueba llama a la función 500 000 veces, los resultados pueden ampliar en gran medida esa sobrecarga.

Podríamos reducir aún más la sobrecarga moviendo el bucle `for` al código nativo. Esto implicaría usar el [protocolo de iterador](https://docs.python.org/c-api/iter.html) (o el tipo `py::iterable` de PyBind11 para el [parámetro de función](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) para procesar cada elemento. Quitar las transiciones repetidas entre Python y C++ es una manera eficaz de reducir el tiempo que se necesita para procesar la secuencia.

### <a name="troubleshooting"></a>Solucionar problemas

Si recibe un `ImportError` al intentar importar el módulo, es probable que uno de los siguientes problemas sea la causa:

* Al compilar a través de una referencia de proyecto, asegúrese de que las propiedades del proyecto de C++ coincidan con el entorno de Python activado para el proyecto de Python, especialmente los directorios de inclusión y de biblioteca.

* Asegúrese de que el archivo de salida se denomina `superfastcode.pyd`. Un nombre o extensión diferente impedirá que se importe.

* Si instaló el módulo mediante el archivo *setup.py,* compruebe que ejecutó el comando *pip* en el entorno de Python activado para el proyecto de Python. Al expandir el entorno de Python en el Explorador de soluciones debe aparecer una entrada para `superfastcode`.

## <a name="debug-the-c-code"></a>Depurar el código de C++

Visual Studio admite la depuración de código Python y C++ de forma conjunta. En esta sección, se le guía a través del proceso mediante el proyecto **superfastcode**; los pasos son los mismos para el proyecto **superfastcode2**.

1. Haga clic con el botón derecho en el proyecto de Python en el **Explorador de soluciones**, seleccione **Propiedades**, elija la pestaña **Depurar** y, después, seleccione la opción **Depurar** > **Habilitar depuración de código nativo**.

    > [!Tip]
    > Cuando se habilita la depuración de código nativo, la ventana de resultados de Python podría desaparecer de inmediato al completarse el programa, sin ofrecer la pausa habitual **Presione cualquier tecla para continuar**. Para forzar una pausa, agregue la opción `-i` al campo **Ejecutar** > **Argumentos del intérprete** en la pestaña **Depurar** al habilitar la depuración de código nativo. Este argumento coloca al intérprete de Python en modo interactivo cuando finaliza el código, momento en que espera a que presione **Ctrl**+**Z** > **Entrar** para salir. (Como alternativa, si no le importa modificar el código de Python, puede agregar las instrucciones `import os` y `os.system("pause")` al final del programa. Este código duplica la petición de pausa original).

1. Seleccione **Archivo** > **Guardar** para guardar los cambios de propiedad.

1. Establezca la configuración de compilación como **Depurar** en la barra de herramientas de Visual Studio.

    ![Establecer la configuración de compilación como Depurar](media/cpp-set-debug.png)

1. Puesto que el código normalmente tarda más tiempo en ejecutarse en el depurador, puede que le interese cambiar la variable `COUNT` del archivo *.py* a un valor que sea unas cinco veces más pequeño (por ejemplo, cambiarlo de `500000` a `100000`).

1. En el código de C++, establezca un punto de interrupción en la primera línea del método `tanh_impl` e inicie el depurador (**F5** o **Depurar** > **Iniciar depuración**). El depurador se detendrá cuando se realice la llamada a ese código. Si no se alcanza el punto de interrupción, compruebe que la configuración esté establecida como **Depurar** y que haya guardado el proyecto (esto no se realiza automáticamente al iniciar al depurador).

    ![Detener en un punto de interrupción en el código de C++](media/cpp-debugging.png)

1. En este punto puede recorrer el código de C++, examinar las variables, etc. Estas características se detallan en [Depurar Python y C++ de forma conjunta](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Enfoques alternativos

Existen diversos métodos para crear extensiones de Python, como se describe en la tabla siguiente. Las dos primeras entradas de `CPython` y `PyBind11` son lo que ya se ha tratado en este artículo.

| Enfoque | Vintage | Usuarios representativos | 
| --- | --- | --- |
| Módulos de extensión de C/C++ para `CPython` | 1991 | biblioteca estándar | 
| [PyBind11](https://github.com/pybind/pybind11) (recomendado para C++) | 2015 |  |
| [Cython](https://cython.org) (recomendado para C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [cryptography](https://cryptography.io/), [pypy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Consulte también

El ejemplo completo de este tutorial se puede encontrar en [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

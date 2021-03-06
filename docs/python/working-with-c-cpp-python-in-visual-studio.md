---
title: Escritura de extensiones de C++ para Python
description: En este artículo se explica cómo crear una extensión de C++ para Python mediante Visual Studio, CPython y PyBind11, incluida la depuración en modo mixto.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973445"
---
# <a name="create-a-c-extension-for-python"></a>Creación de una extensión de C++ para Python

Los módulos escritos en C++ (o C) se usan normalmente para ampliar las funciones de un intérprete de Python. También se usan para habilitar el acceso a las funcionalidades de sistema operativo de bajo nivel. 

Hay tres tipos principales de módulos:

- **Módulos de acelerador**: como Python es un lenguaje interpretado, puede escribir módulos de acelerador en C++ para un mayor rendimiento.
- **Módulos de contenedor**: exponen las interfaces de C o C++ existentes a código de Python, o bien exponen una API más propia de Python que se pueda usar fácilmente con este código.
- **Módulos de acceso al sistema de bajo nivel**: puede crear estos módulos para acceder a características de bajo nivel del tiempo de ejecución de `CPython`, el sistema operativo o el hardware subyacente.

Este artículo le guía por la compilación de un módulo de extensión de C++ para `CPython` que calcula la tangente hiperbólica y la llama desde código de Python. Primero, se implementa la rutina en Python para demostrar la mejora relativa del rendimiento de la implementación de la misma rutina en C++.

En este artículo también se muestran dos formas de hacer que la extensión de C++ esté disponible para Python:

- Usar las extensiones de `CPython` estándar, como se describe en la [documentación de Python](https://docs.python.org/3/c-api/).
- Usar [PyBind11](https://github.com/pybind/pybind11), que es la recomendación para C++11 debido a su sencillez.

Encontrará el ejemplo completo de este tutorial en GitHub, en [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

## <a name="prerequisites"></a>Prerrequisitos

- Visual Studio 2017 o posterior, con la carga de trabajo Desarrollo de Python instalada. La carga de trabajo incluye las herramientas de desarrollo nativas de Python, que proporcionan la carga de trabajo de C++ y los conjuntos de herramientas necesarios para las extensiones nativas.

    ![Captura de pantalla de una lista de opciones de desarrollo de Python, en la que se resalta la opción Herramientas de desarrollo nativo de Python.](media/cpp-install-native.png)

    > [!NOTE]
    > Al instalar la carga de trabajo **Aplicaciones de ciencia de datos y de análisis**, se instalan de forma predeterminada Python y la opción **Herramientas de desarrollo nativo de Python**.

Para obtener más información sobre las opciones de instalación, vea [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md). Si instala Python por separado, asegúrese de seleccionar **Download debugging symbols** (Descargar símbolos de depuración) en **Opciones avanzadas** en el programa de instalación. Esta opción es necesaria para usar la depuración en modo mixto entre el código de Python y el código nativo.

## <a name="create-the-python-application"></a>Crear la aplicación de Python

1. Cree un proyecto de Python en Visual Studio. Para ello, seleccione **Archivo** > **Nuevo** > **Proyecto**. Busque **Python**, seleccione la plantilla **Aplicación de Python**, escriba un nombre y una ubicación, y seleccione **Aceptar**.

1. En el archivo *.py* del proyecto, pegue el código siguiente. Para experimentar algunas de las [características de edición de Python](editing-python-code-in-visual-studio.md), pruebe a escribir el código manualmente.  

   Este código calcula una tangente hiperbólica sin usar la biblioteca matemática, y es lo que se acelerará con las extensiones nativas.

    > [!Tip]
    > Escriba el código en Python puro antes de volver a escribirlo en C++. De este modo, puede comprobar más fácilmente que el código nativo es correcto.

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

1. Para ver los resultados, seleccione **Depurar** > **Iniciar sin depurar** o presione Ctrl+F5 para ejecutar el programa. 

   Puede ajustar la variable `COUNT` para cambiar el tiempo que tarda en ejecutarse la prueba comparativa. Para los fines de este tutorial, establezca el contador para que la prueba comparativa tarde aproximadamente dos segundos.

   > [!TIP]
   > Al ejecutar pruebas comparativas, use siempre **Depurar** > **Iniciar sin depurar**. Esto ayuda a evitar la sobrecarga que se genera al ejecutar el código dentro del depurador de Visual Studio.

## <a name="create-the-core-c-projects"></a>Crear los proyectos principales de C++

Siga las instrucciones de esta sección para crear dos proyectos de C++ idénticos, *superfastcode* y *superfastcode2*. Más adelante, usará un enfoque distinto en cada proyecto para exponer el código de C++ en Python.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución y seleccione **Agregar** > **Nuevo proyecto**. Una solución de Visual Studio puede contener proyectos de Python y C++, una de las ventajas de utilizar Visual Studio para Python.

1. Busque **C++** , seleccione **Proyecto vacío**, especifique **superfastcode** para el primer proyecto o **superfastcode2** para el segundo y, después, seleccione **Aceptar**.

    > [!Tip]
    > Como alternativa, con las herramientas de desarrollo nativo de Python instaladas en Visual Studio, puede comenzar con la plantilla Módulo de extensión de Python. La plantilla ya incluye gran parte de lo que se describe a continuación. 
    > 
    > En este tutorial partiremos de un proyecto vacío para mostrar la compilación del módulo de extensión paso a paso. Después de comprender el proceso, puede usar la plantilla para ahorrar tiempo cuando escriba extensiones propias.

1. Para crear un archivo de C++ en el nuevo proyecto, haga clic con el botón derecho en el nodo **Archivos de origen** y, después, seleccione **Agregar** > **Nuevo elemento**.

1. Seleccione **Archivo de C++** , asígnele el nombre *module.cpp* y, después, seleccione **Aceptar**.

    > [!Important]
    > Para activar las páginas de propiedades de C++ en los pasos siguientes, es necesario un archivo con la extensión *.cpp*.

1. En la barra de herramientas principal, use el menú desplegable para realizar una de las acciones siguientes:

   * Para un entorno de ejecución de Python de 64 bits, active la configuración de **x64**. 
   * Para un entorno de ejecución de Python de 32 bits, active la configuración de **Win32**.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de C++, seleccione **Propiedades** y, después, haga lo siguiente: 

   a. En **Configuración**, escriba **Activo (Depurar)** .  
   b. En **Plataforma**, escriba **Activo (x64)** o **Activo (Win32)** , en función de la selección del paso anterior.

    > [!NOTE]
    > Al crear proyectos propios, querrá establecer las configuraciones de *depuración* y *versión*. En esta unidad, solo se configura la configuración de depuración y se establece para usar una compilación de versión de CPython. Esta configuración deshabilita algunas características de depuración del tiempo de ejecución de C++, incluidas las aserciones. Para usar archivos binarios de depuración de CPython (*python_d.exe*) se necesita otra configuración.

1. Establezca las propiedades como se describe en la tabla siguiente:

    ::: moniker range=">=vs-2019"

    | Pestaña | Propiedad | Valor |
    | --- | --- | --- |
    | **General** | **Nombre de destino** | Especifique el nombre del módulo para hacerle referencia desde Python en las instrucciones `from...import`. Use este mismo nombre en el código de C++ al definir el módulo para Python. Para usar el nombre del proyecto como nombre del módulo, deje el valor predeterminado **$\<ProjectName>** .  Para `python_d.exe`, agregue `_d` al final del nombre. |
    | | **Tipo de configuración** | **Biblioteca dinámica (.dll)** |
    | | **Opciones avanzadas** > **Extensión de archivo de destino** | **.pyd** |
    | | **Valores predeterminados del proyecto** > **Tipo de configuración** | **Biblioteca dinámica (.dll)** |
    | **C/C++** > **General** | **Directorios de inclusión adicionales** | Agregue la carpeta *include* de Python según sea necesario para la instalación (por ejemplo, `c:\Python36\include`).  |
    | **C/C++** > **Preprocesador** | **Definiciones de preprocesador** | Si está presente, cambie el valor **_DEBUG** por **NDEBUG** para que coincida con la versión que no es de depuración de CPython. Si usa *python_d.exe*, no cambie este valor. |
    | **C/C++** > **Generación de código** | **Biblioteca en tiempo de ejecución** | **DLL multiproceso (/MD)** para que coincida con la versión que no es de depuración de CPython. Si usa *python_d.exe*, deje este valor como **DLL de depuración multiproceso (/MDd)** . |
    | **Enlazador** > **General** | **Directorios de bibliotecas adicionales** | Agregue la carpeta *libs* de Python que contiene archivos *.lib* según sea necesario para la instalación (por ejemplo, *c:\Python36\libs*). Asegúrese de apuntar a la carpeta *libs* que contiene los archivos *.lib*, y *no* a la carpeta *Lib* que contiene los archivos *.py*. |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Pestaña | Propiedad | Valor |
    | --- | --- | --- |
    | **General** | **General** > **Nombre de destino** | Especifique el nombre del módulo para hacerle referencia desde Python en las instrucciones `from...import`. Use este mismo nombre en el código de C++ al definir el módulo para Python. Para usar el nombre del proyecto como nombre del módulo, deje el valor predeterminado **$\<ProjectName>** . Para `python_d.exe`, agregue `_d` al final del nombre. |
    | | **General** > **Extensión de destino** | **.pyd** |
    | | **Valores predeterminados del proyecto** > **Tipo de configuración** | **Biblioteca dinámica (.dll)** |
    | **C/C++** > **General** | **Directorios de inclusión adicionales** | Agregue la carpeta *include* de Python según sea necesario para la instalación; (por ejemplo, *c:\Python36\include*).  |
    | **C/C++** > **Preprocesador** | **Definiciones de preprocesador** | Si está presente, cambie el valor **_DEBUG** por **NDEBUG** para que coincida con la versión que no es de depuración de `CPython`. Cuando use `python_d.exe`, deje este valor sin cambios. |
    | **C/C++** > **Generación de código** | **Biblioteca en tiempo de ejecución** | **DLL multiproceso (/MD)** para que coincida con la versión que no es de depuración de `CPython`. Cuando use `python_d.exe`, deje este valor sin cambios. |
    | **Enlazador** > **General** | **Directorios de bibliotecas adicionales** | Agregue la carpeta *libs* de Python que contiene archivos *.lib* según sea necesario para la instalación (por ejemplo, *c:\Python36\libs*). Asegúrese de apuntar a la carpeta *libs* que contiene los archivos *.lib*, y *no* a la carpeta *Lib* que contiene los archivos *.py*. |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > Si la pestaña **C/C++** no se muestra en las propiedades del proyecto, el proyecto no contiene ningún archivo que identifique como archivos de código fuente de C/C++. Esta condición se puede producir si crea un archivo de código fuente sin una extensión *.c* o *.cpp*. 
    > 
    > Por ejemplo, si ha escrito accidentalmente *module.coo* en lugar de *module.cpp* en el anterior cuadro de diálogo Nuevo elemento, Visual Studio crea el archivo, pero no establece el tipo de archivo en *Código de C/C++* , que es lo que activa la pestaña de propiedades de C/C++. Este error de identificación se mantiene incluso si cambia el nombre del archivo con una extensión *.cpp*. 
    > 
    > Para establecer el tipo de archivo correctamente, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Propiedades**. Después, en **Tipo de archivo**, seleccione **Código de C/C++** .

1. Seleccione **Aceptar**.

1. Para probar las configuraciones (tanto de *Depuración* como de *Versión*), haga clic con el botón derecho en el proyecto de C++ y seleccione **Compilar**. 

   Encontrará los archivos *.pyd* en la carpeta *solution* de *Depuración* y *Versión*, no en la carpeta del proyecto de C++.

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

1. Si todavía no lo ha hecho, repita los pasos anteriores para crear un segundo proyecto denominado *superfastcode2* con una configuración idéntica.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Convertir los proyectos de C++ en extensiones para Python

Para convertir el archivo DLL de C++ en una extensión para Python, primero debe modificar los métodos exportados para que interactúen con tipos de Python. Después, debe agregar una función que exporte el módulo, junto con las definiciones de los métodos del módulo.

En las secciones siguientes se explica cómo realizar estos pasos con las extensiones CPython y PyBind11.

### <a name="use-cpython-extensions"></a>Uso de las extensiones CPython

Para obtener más información sobre el código que se muestra en esta sección, vea el [Manual de referencia de la API de Python/C](https://docs.python.org/3/c-api/index.html) y, en concreto, la página [Objetos de módulo](https://docs.python.org/3/c-api/module.html). Asegúrese de seleccionar la versión de Python en la lista desplegable de la esquina superior derecha.

1. En la parte superior del archivo *module.cpp*, incluya *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Modifique el método `tanh_impl` para aceptar y devolver tipos de Python (es decir, `PyObject*`):

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

1. Agregue una estructura que defina el módulo como quiera que se haga referencia a él en el código de Python, en concreto cuando use la instrucción `from...import`. 

   El nombre que se importa en este código debe coincidir con el valor de las propiedades del proyecto en **Propiedades de configuración** > **General** > **Nombre del destino**. 

   En el ejemplo siguiente, el nombre de módulo `"superfastcode"` significa que puede usar `from superfastcode import fast_tanh` en Python, porque `fast_tanh` se define en `superfastcode_methods`. Los nombres de archivo que son internos del proyecto de C++, como *module.cpp*, no son esenciales.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Agregue un método al que Python llame cuando cargue el módulo, que debe denominarse `PyInit_<module-name>`, donde *\<module-name>* coincide exactamente con la propiedad **General** > **Nombre de destino** del proyecto de C++. Es decir, coincide con el nombre del archivo *.pyd* creado por el proyecto.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compile de nuevo el proyecto de C++ para verificar el código. Si se producen errores, vea la sección ["Solución de problemas"](#troubleshoot-compiling-failures).

### <a name="use-pybind11"></a>Uso de PyBind11

Si ha completado los pasos descritos en la sección anterior, sin duda ha observado que usa una gran cantidad de código reutilizable para crear las estructuras de módulo necesarias para el código de C++. PyBind11 simplifica el proceso mediante macros en un archivo de encabezado de C++ que consigue el mismo resultado, pero con mucho menos código. 

Para obtener más información sobre el código de esta sección, vea [Conceptos básicos de PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst).

1. Instale PyBind11 mediante pip: `pip install pybind11` o `py -m pip install pybind11`. 

   Como alternativa, puede instalar PyBind11 con la ventana Entornos de Python y, después, usar su comando **Abrir en PowerShell** para el paso siguiente.

1. En el mismo terminal, ejecute `python -m pybind11 --includes` o `py -m pybind11 --includes`. 

   Esto imprime una lista de rutas de acceso que debe agregar a la propiedad **C/C++**  > **General** > **Directorios de inclusión adicionales** del proyecto. Asegúrese de quitar el prefijo `-I`, si está presente.

1. En la parte superior de un archivo *module.cpp* nuevo que no incluya ninguno de los cambios de la sección anterior, incluya *pybind11.h*:

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

1. Compile el proyecto de C++ para verificar el código. Si se producen errores, vea la sección siguiente, "Solución de problemas de compilación", para obtener soluciones.

### <a name="troubleshoot-compiling-failures"></a>Solución de problemas de compilación

Es posible que se produzca un error de compilación en el módulo de C++ por las razones siguientes:

- Error: No se puede encontrar *Python.h* (**E1696: no se puede abrir el archivo de código fuente "Python.h"** o **C1083: No se puede abrir el archivo de inclusión: "Python.h": no existe en archivo o directorio**) 

  Solución: compruebe que la ruta de acceso de **C/C++**  > **General** > **Directorios de inclusión adicionales** de las propiedades del proyecto apunta a la carpeta *include* de la instalación de Python. Consulte el paso 6 en [Crear el proyecto de C++ principal](#create-the-core-c-projects).

- Error: No se pueden encontrar las bibliotecas de Python 
 
   Solución: compruebe que la ruta de acceso de **C/C++**  > **General** > **Directorios de biblioteca adicionales** de las propiedades del proyecto apunta a la carpeta *libs* de la instalación de Python. Consulte el paso 6 en [Crear el proyecto de C++ principal](#create-the-core-c-projects).

- Errores del enlazador relacionados con la arquitectura de destino
   
   Solución: cambie la arquitectura del proyecto del destino de C++ para que coincida con la de la instalación de Python. Por ejemplo, si el destino es Win32 con el proyecto de C++, pero la instalación de Python es de 64 bits, cambie el proyecto de C++ a x64.

## <a name="test-the-code-and-compare-the-results"></a>Probar el código y comparar los resultados

Ahora que tiene los archivos DLL estructurados como extensiones de Python, puede hacerles referencia desde el proyecto de Python, importar los módulos y usar sus métodos.

### <a name="make-the-dll-available-to-python"></a>Poner el archivo DLL a disposición de Python

Puede hacer que el archivo DLL esté disponible para Python de varias maneras. Estos son dos enfoques que se deben tener en cuenta: 

* Este primer método funciona si el proyecto de Python y el de C++ se encuentran en la misma solución. Haga lo siguiente: 

   1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Referencias** del proyecto de Python y, después, seleccione **Agregar referencia**. 
   1. En el cuadro de diálogo que aparecerá, seleccione la pestaña **Proyectos**, los proyectos **superfastcode** y **superfastcode2** y **Aceptar**.

      ![Captura de pantalla en la que se muestra cómo agregar una referencia al proyecto "superfastcode".](media/cpp-add-reference.png)

* Un método alternativo instala el módulo en el entorno de Python, lo que hace que el módulo también esté disponible para otros proyectos de Python. Para obtener más información, vea la [Documentación del proyecto **setuptools**](https://setuptools.readthedocs.io/). Haga lo siguiente:

    1. Cree un archivo denominado *setup.py* en el proyecto de C++; para ello, haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **Nuevo elemento**. 
    
    1. Seleccione **Archivo de C++ (.cpp)** , asigne el nombre *setup.py* al archivo y, después, seleccione **Aceptar**.
    
       Al asignar un nombre al archivo con la extensión *.py*, Visual Studio lo reconoce como un archivo de Python a pesar del uso de la plantilla de archivo de C++. 

       Cuando el archivo aparezca en el editor, pegue el código siguiente en él, en función de lo que corresponda al método de extensión:
    
        **Para las extensiones de `CPython` (proyecto superfastcode)** :
    
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
    
        **Para `PyBind11` (proyecto superfastcode2)** :
    
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
    
    1. Cree un segundo archivo denominado *pyproject.toml* en el proyecto de C++ y pegue el código siguiente en él:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Para compilar la extensión, haga clic con el botón derecho en la pestaña *pyproject.toml* abierta y, después, seleccione **Copiar ruta de acceso completa**. Eliminará el nombre *pyproject.toml* de la ruta de acceso antes de usarla.
    
    1. En el **Explorador de soluciones**, haga clic con el botón derecho en el entorno de Python activo y seleccione **Administrar paquetes de Python**.
    
        > [!Tip]
        > Si ya ha instalado el paquete, verá que aparece aquí. Antes de continuar, haga clic en la **X** para desinstalarlo.
    
    1. En el cuadro de búsqueda, pegue la ruta de acceso copiada, elimine *pyproject.toml* de la parte final y, después, presione Entrar para instalar el módulo desde ese directorio.
    
        > [!Tip]
        > Si se produce un error en la instalación debido a un error de permisos, agregue *--user* al final y vuelva a probar el comando.


### <a name="call-the-dll-from-python"></a>Llamar al archivo DLL desde Python

Una vez que el archivo DLL está disponible para Python, como se ha descrito en la sección anterior, puede llamar a las funciones `superfastcode.fast_tanh` y `superfastcode2.fast_tanh2` desde el código de Python y comparar su rendimiento con la implementación de Python. Para llamar al archivo DLL, haga lo siguiente:

1. Agregue las líneas siguientes en el archivo *.py* para llamar a los métodos que se han exportado desde los archivos DLL y mostrar sus salidas:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Para ejecutar el programa de Python, seleccione **Depurar** > **Iniciar sin depurar** o presione Ctrl+F5.

    > [!NOTE]
    > Si el comando **Iniciar sin depurar** está deshabilitado, haga clic con el botón derecho en el proyecto de Python en el **Explorador de soluciones** y seleccione **Establecer como proyecto de inicio**.  

    Observe que las rutinas de C++ se ejecutan aproximadamente de cinco a veinte veces más rápido que la implementación de Python. El resultado típico se muestra de la manera siguiente:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Intente aumentar la variable `COUNT` para que las diferencias sean más pronunciadas. 

    Una compilación de *depuración* del módulo de C++ también se ejecuta de forma más lenta que una compilación de *versión*, ya que la de depuración está menos optimizada y contiene varias comprobaciones de errores. No dude en cambiar entre esas configuraciones para ver la comparación, pero recuerde volver y actualizar las propiedades que ha establecido antes para la configuración de versión.

En la salida, es posible que vea que la extensión de PyBind11 no es tan rápida como la de CPython, aunque debería ser mucho más rápida que la implementación pura de Python. Esta diferencia se debe en gran medida a que ha usado la llamada `METH_O`, que no admite varios parámetros, nombres de parámetros o argumentos de palabras clave. PyBind11 genera código ligeramente más complejo para proporcionar a los autores de la llamada una interfaz más similar a Python. Pero como el código de prueba llama 500 000 veces a la función, es posible que los resultados aumenten considerablemente esa sobrecarga.

Podría reducir todavía más la sobrecarga si mueve el bucle `for` al código nativo. Este enfoque supondría usar el [protocolo de iterador](https://docs.python.org/c-api/iter.html) (o el tipo `py::iterable` de PyBind11 para el [parámetro de función](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) a fin de procesar cada elemento. Quitar las transiciones repetidas entre Python y C++ es una manera eficaz de reducir el tiempo que se necesita para procesar la secuencia.

### <a name="troubleshoot-importing-errors"></a>Solución de problemas de importación

Si recibe un mensaje `ImportError` al intentar importar el módulo, puede resolverlo de una de las maneras siguientes:

* Al realizar la compilación mediante una referencia de proyecto, asegúrese de que las propiedades del proyecto de C++ coincidan con el entorno de Python activado para el proyecto de Python, especialmente los directorios *Include* y *Library*.

* Asegúrese de que el archivo de salida se denomina *superfastcode.pyd*. Cualquier otro nombre o extensión impedirá que se importe.

* Si ha instalado el módulo mediante el archivo *setup.py*, compruebe que ha ejecutado el comando *pip* en el entorno de Python activado para el proyecto de Python. Al expandir el entorno de Python en el Explorador de soluciones se debe mostrar una entrada para *superfastcode*.

## <a name="debug-the-c-code"></a>Depurar el código de C++

Visual Studio admite la depuración de código Python y C++ de forma conjunta. En esta sección, recorrerá el proceso mediante el proyecto *superfastcode*. El proceso es el mismo para el proyecto *superfastcode2*.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de Python, seleccione **Propiedades**, elija la pestaña **Depurar** y, después, seleccione la opción **Depurar** > **Habilitar depuración de código nativo**.

    > [!Tip]
    > Al habilitar la depuración de código nativo, la ventana de salida de Python podría cerrarse de inmediato al completarse el programa, sin ofrecer la pausa habitual **Presione cualquier tecla para continuar**. 
    >
    > Solución: para forzar una pausa después de habilitar la depuración de código nativo, agregue la opción `-i` al campo **Ejecutar** > **Argumentos del intérprete** de la pestaña **Depurar**. Este argumento coloca el intérprete de Python en modo interactivo después de ejecutar el código, momento en el que espera a que presione Ctrl+Z y después Entrar para cerrar la ventana. 
    >
    > Como alternativa, si no le importa modificar el código de Python, puede agregar instrucciones `import os` y `os.system("pause")` al final del programa. Este código duplica la petición de pausa original.

1. Seleccione **Archivo** > **Guardar** para guardar los cambios de propiedad.

1. En la barra de herramientas de Visual Studio, establezca la configuración de compilación en **Depuración**.

    ![Captura de pantalla de la configuración "Depuración" en la barra de herramientas de Visual Studio.](media/cpp-set-debug.png)

1. Como normalmente el código tarda más tiempo en ejecutarse en el depurador, puede que le interese cambiar la variable `COUNT` del archivo *.py* por un valor que sea unas cinco veces más pequeño que el predeterminado. Por ejemplo, puede cambiarlo de **500 000** a **100 000**.

1. En el código de C++, establezca un punto de interrupción en la primera línea del método `tanh_impl` y, después, presione **F5** o seleccione **Depurar** > **Iniciar depuración** para iniciar el depurador. 

    El depurador se detendrá cuando se llame al punto de interrupción. Si no se alcanza el punto de interrupción, compruebe que la configuración esté establecida en **Depuración** y que ha guardado el proyecto, lo que no se realiza automáticamente al iniciar al depurador.

    ![Captura de pantalla del código de C++ que contiene un punto de interrupción.](media/cpp-debugging.png)

1. En el punto de interrupción, puede ejecutar paso a paso el código de C++, examinar las variables, etc. Para obtener más información sobre estas características, vea [Depuración conjunta de Python y C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Enfoques alternativos

Existen diversos métodos para crear extensiones de Python, como se describe en la tabla siguiente. En este artículo se describen las dos primeras filas, `CPython` y `PyBind11`.

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

Encontrará el ejemplo completo de este tutorial en GitHub, en [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

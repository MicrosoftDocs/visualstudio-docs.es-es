---
title: Código de pruebas unitarias de Python
description: La configuración de pruebas unitarias para código de Python en Visual Studio aprovecha al máximo las características del Explorador de pruebas con el fin de detectar, ejecutar y depurar las pruebas.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6b611657db104a4b74e784df8925627ff41f3c33
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535345"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Selección del marco de pruebas de un proyecto de Python

Visual Studio admite dos marcos de pruebas con Python, [unittest](https://docs.python.org/3/library/unittest.html) y [pytest](https://pytest.org/en/latest/) (disponibles a partir de la versión 16.3 de Visual Studio 2019). Ninguno de los marcos se selecciona de forma predeterminada cuando se crea un proyecto de Python. Para especificar un marco, haga clic con el botón derecho en el nombre del proyecto en el Explorador de soluciones y seleccione **Propiedades**. Se abrirá el diseñador de proyectos, donde puede configurar las pruebas a través de la pestaña **Prueba**. En esta pestaña, puede seleccionar el marco de pruebas que quiere usar en el proyecto. 

* En el marco **unittest**, el directorio raíz del proyecto se usa para la detección de pruebas. Esta ubicación, así como el patrón de texto para identificar pruebas, se pueden modificar en la pestaña **Prueba** por los valores especificados por el usuario.
* En el marco **pytest**, las opciones de prueba como la ubicación de las pruebas y los patrones de nombre de archivo se especifican mediante el archivo de configuración estándar pytest.ini. Vea la [documentación de referencia de pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) para más información.

Una vez que haya guardado la selección y la configuración del marco de trabajo, la detección de pruebas se inicia en el Explorador de pruebas. Si la ventana Explorador de pruebas todavía no está abierta, vaya a la barra de herramientas y seleccione **Prueba** > **Explorador de pruebas**.

## <a name="configure-testing-for-python-without-a-project"></a>Configuración de pruebas para Python sin un proyecto
Visual Studio permite ejecutar y probar el código de Python existente sin un proyecto, simplemente [abriendo una carpeta](../../quickstart-05-python-visual-studio-open-folder.md) con código de Python. En estas circunstancias, deberá usar un archivo **PythonSettings.json** para configurar las pruebas. 
1. Abra el código de Python existente con la opción **Abrir una carpeta local**. 

   ![La pantalla Inicio de Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. En la ventana de Explorador de soluciones, haga clic en el icono **Mostrar todos los archivos** para mostrar todos los archivos de la carpeta actual.

   ![Botón Mostrar todos los archivos](../../media/unit-test-show-files.png)

1. Vaya al archivo **PythonSettings.json** dentro de la carpeta **Configuración local**. Si no ve este archivo en la carpeta **Configuración local**, créelo manualmente.
   
1. Agregue el campo **TestFramework** al archivo de configuración y establézcalo en **pytest** o en **unittest**, según cuál sea el marco de pruebas que quiera usar.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > En el marco **unittest**, si los campos **UnitTestRootDirectory** y **UnitTestPattern** no están especificados en el archivo PythonSettings.json, se agregan y se les asignan los valores predeterminados "." y "test*.py" respectivamente.

1. Si la carpeta contiene un directorio **src** que es independiente de la carpeta que contiene las pruebas, especifique la ruta de acceso a la carpeta **src** mediante el campo **SearchPaths** del archivo **PythonSettings.json**.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Guarde los cambios en el archivo PythonSettings.json para iniciar la detección de pruebas del marco especificado. 
   > [!Note]
   > Si la ventana Explorador de pruebas ya está abierta, **Ctrl** + **R,A** también desencadena la detección.

## <a name="discover-and-view-tests"></a>Detección y visualización de pruebas

Visual Studio identifica de forma predeterminada las pruebas de **unittest** y **pytest** como métodos cuyos nombres empiezan por `test`. Haga lo siguiente para ver la detección de pruebas:

1. Abra un [proyecto de Python](../../managing-python-projects-in-visual-studio.md).

1. Una vez cargado el proyecto en Visual Studio, haga clic con el botón derecho en él en Explorador de soluciones y seleccione el marco **unittest** o **pytest** en las propiedades de la pestaña **Prueba**.
   > [!Note]
   > Si usa el marco pytest, puede especificar la ubicación de las pruebas y los patrones de nombre de archivo mediante el archivo de configuración estándar pytest.ini. De forma predeterminada, se usa la carpeta del proyecto o del área de trabajo, con un patrón de `test_*py` y `*_test.py`. Vea la [documentación de referencia de pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) para más información.

1. Una vez seleccionado el marco, vuelva a hacer clic con el botón derecho en el proyecto, seleccione **Agregar** > **Nuevo elemento** y, después, seleccione **Prueba unitaria de Python** seguido de **Agregar**.

1. Esta acción crea un archivo *test_1.py* con código que importa el módulo estándar `unittest`, deriva una clase de prueba de `unittest.TestCase` e invoca `unittest.main()` si ejecuta el script directamente:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Si es necesario, guarde el archivo y luego abra el **Explorador de pruebas** con el comando de menú **Prueba** > **Explorador de pruebas**.

1. El **Explorador de pruebas** busca las pruebas en el proyecto y las mostrará como se muestra a continuación. Haga doble clic en una prueba para abrir su archivo de origen.

    ![Explorador de pruebas en el que se muestra la prueba test_A predeterminada](../../media/unit-test-a-2.png) 

1. A medida que agrega más pruebas para el proyecto, puede organizar la vista en el **Explorador de pruebas** mediante el menú **Agrupar por** de la barra de herramientas:

    ![Grupo del Explorador de pruebas mediante el menú de la barra de herramientas](../../media/unit-test-group-menu-2.png) 

1. También puede escribir texto en el campo de **búsqueda** para filtrar pruebas por nombre.

Para más información sobre el módulo `unittest` y las pruebas de escritura, vea la [documentación de Python 2.7](https://docs.python.org/2/library/unittest.html) o la [documentación de Python 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Ejecutar pruebas

En el **Explorador de pruebas** puede ejecutar pruebas de varias maneras:

- **Ejecutar todas** claramente ejecuta todas las pruebas mostradas (sujeto a filtros).
- El menú **Ejecutar** proporciona comandos para ejecutar pruebas con error, superadas o no ejecutadas como un grupo.
- Puede seleccionar una o varias pruebas, hacer clic con el botón derecho y seleccionar **Ejecutar pruebas seleccionadas**.

Las pruebas se ejecutan en segundo plano y el **Explorador de pruebas** actualiza el estado de todas las pruebas a medida que se completan:

- Las pruebas superadas muestran una marca de verificación verde y el tiempo dedicado a ejecutar la prueba:

    ![Estado de la prueba test_A superada](../../media/unit-test-A-pass.png)

- Las pruebas con error muestran una cruz roja con un vínculo **Salida** que muestra la salida de la consola y la salida `unittest` de la serie de pruebas:

    ![Estado de la prueba test_A con error](../../media/unit-test-A-fail.png)

    ![test_A con error y un motivo](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Depuración de pruebas

Dado que las pruebas unitarias son fragmentos de código, están sujetas a errores como cualquier otro código y, en ciertas ocasiones, necesitan ejecutarse en un depurador. En el depurador puede establecer puntos de interrupción, examinar variables y recorrer el código. Visual Studio también proporciona herramientas de diagnóstico para las pruebas unitarias.

> [!Note]
> De forma predeterminada, la depuración de prueba usa el depurador de ptvsd 4 para Visual Studio 2017 (versiones 15.8 y posteriores) y debugpy para Visual Studio 2019 (versiones 16.5 y posteriores). Si quiere usar ptvsd 3 en su lugar, puede seleccionar la opción **Usar depurador heredado** en **Herramientas** > **Opciones** > **Python** > **Depuración**. 

Para iniciar la depuración, establezca un punto de interrupción inicial en el código y luego haga clic con el botón derecho en la prueba (o una selección) en el **Explorador de pruebas** y seleccione **Depurar pruebas seleccionadas**. Visual Studio inicia el depurador de Python como lo haría para el código de la aplicación.

![Depuración de una prueba](../../media/unit-test-debugging.png)

También puede usar **Analizar cobertura de código para las pruebas seleccionadas**. Para obtener más información, vea [Usar cobertura de código para determinar la cantidad de código que se está probando](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

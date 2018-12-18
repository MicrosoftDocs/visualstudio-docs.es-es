---
title: Pruebas unitarias para Python
description: Configuración de pruebas unitarias para código de Python en Visual Studio para aprovechar al máximo las características del Explorador de pruebas con el fin de detectar, ejecutar y depurar las pruebas.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e8a3a61b7c77031033c9cdc988753437f25166a1
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607580"
---
# <a name="set-up-unit-testing-for-python-code"></a>Configuración de pruebas unitarias para código de Python

Las pruebas unitarias son fragmentos de código que prueban otras unidades de código de una aplicación, normalmente funciones aisladas, clases, etc. Cuando una aplicación supera todas sus pruebas unitarias, al menos puede confiar en que su función de bajo nivel es correcta.

Python utiliza pruebas unitarias ampliamente para validar escenarios durante el diseño de un programa. La compatibilidad de Python en Visual Studio incluye características para descubrir, ejecutar y depurar pruebas unitarias dentro del contexto de su proceso de desarrollo, sin tener que ejecutar pruebas independientemente.

En este artículo se proporciona una descripción breve de las funcionalidades de las pruebas unitarias en Visual Studio con Python. Para más información sobre las pruebas unitarias en general, vea [Hacer una prueba unitaria del código](../test/unit-test-your-code.md).

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea el vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) sobre pruebas unitarias de Python (2 minutos 31 segundos). |

## <a name="discover-and-view-tests"></a>Detección y visualización de pruebas

Por convención, Visual Studio identifica las pruebas como métodos cuyos nombres empiezan por `test`. Para ver este comportamiento, realice lo siguiente:

1. Abra un [proyecto Python](managing-python-projects-in-visual-studio.md) cargado en Visual Studio, haga clic con el botón derecho en el proyecto, seleccione **Agregar** > **Nuevo elemento** y luego seleccione **Prueba unitaria de Python** y **Agregar**.

1. Esta acción crea un archivo *test1.py* con código que importa el módulo estándar `unittest`, deriva una clase de prueba de `unittest.TestCase` e invoca `unittest.main()` si ejecuta el script directamente:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Si es necesario, guarde el archivo y luego abra el **Explorador de pruebas** con el comando de menú **Prueba** > **Windows** > **Explorador de pruebas**.

1. El **Explorador de pruebas** busca las pruebas en el proyecto y las mostrará como se muestra a continuación. Haga doble clic en una prueba para abrir su archivo de origen.

    ![Explorador de pruebas en el que se muestra la prueba test_A predeterminada](media/unit-test-A.png)

1. A medida que agrega más pruebas para el proyecto, puede organizar la vista en el **Explorador de pruebas** mediante el menú **Agrupar por** de la barra de herramientas:

    ![Grupo del Explorador de pruebas mediante el menú de la barra de herramientas](media/unit-test-group-menu.png)

1. También puede escribir texto en el campo de **búsqueda** para filtrar pruebas por nombre.

Para obtener más información sobre el módulo `unittest` y las pruebas de escritura, vea la [documentación de Python 2.7](https://docs.python.org/2/library/unittest.html) o la [documentación de Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Ejecutar pruebas

En el **Explorador de pruebas** puede ejecutar pruebas de varias maneras:

- **Ejecutar todas** claramente ejecuta todas las pruebas mostradas (sujeto a filtros).
- El menú **Ejecutar** proporciona comandos para ejecutar pruebas con error, superadas o no ejecutadas como un grupo.
- Puede seleccionar una o varias pruebas, hacer clic con el botón derecho y seleccionar **Ejecutar pruebas seleccionadas**.

Las pruebas se ejecutan en segundo plano y el **Explorador de pruebas** actualiza el estado de todas las pruebas a medida que se completan:

- Las pruebas superadas muestran una marca de verificación verde y el tiempo dedicado a ejecutar la prueba:

    ![Estado de la prueba test_A superada](media/unit-test-A-pass.png)

- Las pruebas con error muestran una cruz roja con un vínculo **Salida** que muestra la salida de la consola y la salida `unittest` de la serie de pruebas:

    ![Estado de la prueba test_A con error](media/unit-test-A-fail.png)

    ![test_A con error y un motivo](media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Depuración de pruebas

Dado que las pruebas unitarias son fragmentos de código, están sujetas a errores como cualquier otro código y, en ciertas ocasiones, necesitan ejecutarse en un depurador. En el depurador puede establecer puntos de interrupción, examinar variables y recorrer el código. Visual Studio también proporciona herramientas de diagnóstico para las pruebas unitarias.

Para iniciar la depuración, establezca un punto de interrupción inicial en el código y luego haga clic con el botón derecho en la prueba (o una selección) en el **Explorador de pruebas** y seleccione **Depurar pruebas seleccionadas**. Visual Studio inicia el depurador de Python como lo haría para el código de la aplicación.

![Depuración de una prueba](media/unit-test-debugging.png)

También puede utilizar los comandos **Analizar cobertura de código para las pruebas seleccionadas** y **Generar perfil para pruebas**, según la versión de Visual Studio (consulte la [Matriz de características](overview-of-python-tools-for-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Problemas conocidos

- Al iniciar la depuración, Visual Studio aparece para iniciar y detener la depuración, y luego la inicia de nuevo. Este comportamiento es normal.
- Al depurar varias pruebas, cada una de ellas se ejecuta de manera independiente, lo que interrumpe la sesión de depuración.
- Visual Studio produce un error de manera intermitente al iniciar una prueba durante la depuración. Normalmente, si intenta depurar la prueba de nuevo, la operación se realiza correctamente.
- Al depurar, es posible que salir de una prueba en la implementación de `unittest`. Normalmente, el siguiente paso ejecuta el programa hasta el final y detendrá la depuración.

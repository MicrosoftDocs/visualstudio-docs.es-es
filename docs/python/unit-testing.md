---
title: Pruebas unitarias para Python en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3ad6523-5a4e-4209-8977-adc2da305df2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2597583912c7694495617c53839f41aa13cda871
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="setting-up-unit-testing-for-python-code"></a>Configuración de pruebas unitarias para código Python

Las pruebas unitarias son fragmentos de código que prueban otras unidades de código de una aplicación, normalmente funciones aisladas, clases, etc. Cuando una aplicación supera todas sus pruebas unitarias, al menos puede confiar en que su funcionalidad de bajo nivel es correcta.

Python utiliza pruebas unitarias ampliamente para validar escenarios durante el diseño de un programa. La compatibilidad de Python en Visual Studio incluye características para descubrir, ejecutar y depurar pruebas unitarias dentro del contexto de su proceso de desarrollo, en lugar de tener que ejecutarlas independientemente.

En este tema se proporciona una descripción breve de las funcionalidades de las pruebas unitarias en Visual Studio con Python. Para más información sobre las pruebas unitarias en general, consulte [Haga una prueba unitaria de su código](../test/unit-test-your-code.md).

## <a name="discovering-and-viewing-tests"></a>Detección y visualización de pruebas

Por convención, Visual Studio identifica las pruebas como métodos cuyos nombres empiezan por "test". Para comprender esto, lleve a cabo las acciones siguientes:

1. Abra un [proyecto Python](python-projects.md) cargado en Visual Studio, haga clic con el botón derecho en el proyecto, seleccione **Agregar > Nuevo elemento...** y luego seleccione **Python Unit Test** (Prueba unitaria de Python) y **Agregar**.

1. Esto crea un archivo test1.py con código que importa el módulo estándar `unittest`, deriva una clase de prueba de `unittest.TestCase` e invoca `unittest.main()` si ejecuta el script directamente:

  ```python
  import unittest

  class Test_test1(unittest.TestCase):
      def test_A(self):
          self.fail("Not implemented")

  if __name__ == '__main__':
      unittest.main()
  ```

1. Si es necesario, guarde el archivo y luego abra el Explorador de pruebas con el comando de menú **Prueba > Windows > Explorador de pruebas**.

1. El Explorador de pruebas buscará las pruebas en el proyecto y las mostrará como se indica a continuación. Haga doble clic en una prueba para abrir su archivo de origen.

    ![Explorador de pruebas en el que se muestra la prueba test_A predeterminada](~/python/media/unit-test-A.png)

1. A medida que agrega más pruebas para el proyecto, puede organizar la vista en el Explorador de pruebas mediante el grupo de menú en la barra de herramientas:

    ![Grupo del Explorador de pruebas mediante el menú de la barra de herramientas](~/python/media/unit-test-group-menu.png)

1. También puede escribir texto en el campo de búsqueda para filtrar pruebas por nombre.

Para más detalles sobre el módulo `unittest` y las pruebas de escritura, consulte la [documentación de Python 2.7](https://docs.python.org/2/library/unittest.html) o la [documentación de Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Ejecutar pruebas

En el Explorador de pruebas puede ejecutar pruebas de varias maneras:

- **Ejecutar todas** claramente ejecuta todas las pruebas mostradas (sujeto a filtros).
- El menú **Ejecutar...**  proporciona comandos para ejecutar pruebas con error, superadas o no ejecutadas como un grupo.
- Puede seleccionar una o varias pruebas, hacer clic con el botón derecho y seleccionar **Ejecutar pruebas seleccionadas**.

Las pruebas se ejecutan en segundo plano y el Explorador de pruebas actualiza el estado de todas las pruebas a medida que se completan:

- Las pruebas superadas muestran una marca de verificación verde y el tiempo dedicado a ejecutar la prueba:

    ![Estado de la prueba test_A superada](~/python/media/unit-test-A-pass.png)

- Las pruebas con error muestran una cruz roja con un vínculo **Salida** que muestra la salida de la consola y la salida `unittest` de la serie de pruebas:

    ![Estado de la prueba test_A con error](~/python/media/unit-test-A-fail.png)

    ![test_A con error y un motivo](~/python/media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Depuración de pruebas

Dado que las pruebas unitarias son fragmentos de código, están sujetas a errores como cualquier otro código y, en ciertas ocasiones, necesitan ejecutarse en un depurador, donde puede establecer puntos de interrupción, examinar variables y recorrer el código. Visual Studio también proporciona herramientas de diagnóstico

Para iniciar la depuración, establezca un punto de interrupción inicial en el código y luego haga clic con el botón derecho en la prueba (o una selección) en el Explorador de pruebas y seleccione **Depurar pruebas seleccionadas**. Visual Studio iniciará al depurador de Python como lo haría para el código de la aplicación.

![Depuración de una prueba](~/python/media/unit-test-debugging.png)

También puede utilizar los comandos **Analizar cobertura de código para las pruebas seleccionadas** y **Generar perfil para pruebas**, según la versión de Visual Studio (consulte la [Matriz de características](python-in-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Problemas conocidos

- Al iniciar la depuración, Visual Studio aparece para iniciar y detener la depuración, y luego la inicia de nuevo. Esto es normal.
- Al depurar varias pruebas, cada una de ellas se ejecuta de forma independiente, lo que interrumpirá la sesión de depuración.
- Visual Studio dará error de forma intermitente al iniciar una prueba durante la depuración. Normalmente, si intenta depurar la prueba de nuevo, la operación se realizará correctamente.
- Al depurar, es posible que salir de una prueba en la implementación de `unittest`. Normalmente, el siguiente paso ejecutará el programa hasta el final y detendrá la depuración.

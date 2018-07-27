---
title: Escribir pruebas unitarias para C/C++ en Visual Studio
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: da826928ff44d306c72f330b8221361579840d6a
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235443"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Escribir pruebas unitarias para C/C++ en Visual Studio

Igual que con otros lenguajes, puede escribir y ejecutar pruebas unitarias de C++ en la ventana **Explorador de pruebas**. Para más información sobre cómo usar el **Explorador de pruebas**, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> C++ no admite algunas características, como Live Unit Testing, las pruebas de IU codificadas e IntelliTest.

Visual Studio incluye estos marcos de pruebas de C++ sin que sea preciso descargar nada más:

- Marco de pruebas unitarias de Microsoft para C++
- Google Test
- Boost.Test
- CTest

Además de los marcos instalados, puede escribir su propio adaptador de prueba para cualquier marco de trabajo que quiera usar en Visual Studio. Un adaptador de prueba puede integrar pruebas unitarias con la ventana **Explorador de pruebas**. En [Visual Studio Marketplace](https://marketplace.visualstudio.com) hay disponibles varios adaptadores de terceros. Para más información, vea [Instalar marcos de prueba unitaria de terceros](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017, versión 15.5**

- **Google Test** se incluye como un componente predeterminado de la carga de trabajo de **Desarrollo para el escritorio con C++**. Tiene una plantilla de proyecto que se puede agregar a una solución a través del menú contextual **Agregar nuevo proyecto** del nodo de solución en el **Explorador de soluciones**, así como opciones que se pueden configurar por medio de **Herramientas | Opciones de**. Para más información, vea [Cómo usar Google Test para C++ en Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** se incluye como un componente predeterminado de la carga de trabajo de **Desarrollo para el escritorio con C++**. Se integra con el **Explorador de pruebas**, pero actualmente no tiene plantilla de proyecto, por lo que se debe configurar manualmente. Para más información, vea [Cómo usar Boost.Test para C++ en Visual Studio](how-to-use-boost-test-for-cpp.md).

- La compatibilidad con **CTest** se incluye con el componente [CMake Tools para Visual Studio](/cpp/ide/cmake-tools-for-visual-cpp), que forma parte de la carga de trabajo de **Desarrollo para el escritorio con C++**. Con todo, CTest aún no está totalmente integrado con el **Explorador de pruebas**. Para más información, vea [Cómo usar Google Test para C++ en Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 y anterior**

Puede descargar las extensiones de los adaptadores Google Test y Boost.Test en Visual Studio Marketplace, en las páginas de [Test Adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) y [Test Adapter para Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Flujo de trabajo de prueba básico

En las siguientes secciones se explican los pasos básicos que sirven para empezar a realizar pruebas unitarias de C++. La configuración básica es muy similar en los marcos de Microsoft y Google Test. Boost.Test, por su parte, requiere que se cree un proyecto de prueba manualmente.

### <a name="create-a-test-project"></a>Crear un proyecto de prueba

Hay que definir y ejecutar pruebas en uno o varios proyectos de prueba que estén en la misma solución que el código que quiere probar. Para agregar un nuevo proyecto de prueba a una solución existente, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Agregar | Nuevo proyecto**. Después, en el panel izquierdo, elija **Prueba de Visual C++** y elija uno de los tipos de proyecto en el panel central. En la siguiente ilustración se muestran los proyectos de prueba que hay disponibles cuando se instala la carga de trabajo de **desarrollo para el escritorio con C++**:

![Proyectos de prueba de C++](media/cpp-new-test-project.png)

### <a name="create-references-to-other-projects-in-the-solution"></a>Crear referencias a otros proyectos en la solución

Para permitir que el código de prueba tenga acceso a las funciones en el proyecto que se va a probar, agregue una referencia al proyecto en el proyecto de prueba. Haga clic con el botón secundario en el nodo de proyecto de prueba en el **Explorador de soluciones** y elija **Agregar | Referencia**. Luego, en el cuadro de diálogo, seleccione los proyectos que quiera probar.

![Agregar referencia](media/cpp-add-ref-test-project.png)

### <a name="add-include-directives-for-header-files"></a>Agregar directivas #include de archivos de encabezado

Después, en el archivo .cpp de prueba unitaria, agregue una directiva `#include` relativa a cualquier archivo de encabezado que declare los tipos y funciones que quiera probar. Escriba `#include "` y, de este modo, IntelliSense se activará para ayudarle a elegir. Repita esto mismo con los encabezados que haya.

![Agregar directivas include](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>Escribir métodos de prueba

> [!NOTE]
> En esta sección se muestra la sintaxis del marco de pruebas unitarias de Microsoft para C y C++. Esto se documenta aquí: [Referencia de API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Para ver documentación sobre Google Test, vea [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Si le interesa Boost.Test, vea [Boost Test Library: The Unit Test Framework](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Biblioteca de Boost.Test: el marco de pruebas unitarias).

El archivo .cpp del proyecto de prueba tiene un método y una clase de código auxiliar definidos automáticamente para que pueda ver un ejemplo de cómo escribir código de prueba. Observe que las firmas usan las macros TEST_CLASS y TEST_METHOD, lo que hace que los métodos se puedan detectar desde la ventana Explorador de pruebas.

![Agregar directivas include](media/cpp-write-test-methods.png)

TEST_CLASS y TEST_METHOD forman parte del [Marco de pruebas nativo de Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). El **Explorador de pruebas** detecta métodos de prueba en otros marcos admitidos de forma similar.

Un método TEST_METHOD no devuelve ningún valor. Para obtener un resultado de prueba, use los métodos estáticos de la clase `Assert` para probar resultados reales con lo que se espera. En el siguiente ejemplo, se da por hecho que `MyClass` tiene un constructor que toma una cadena `std::string`. Podemos probar que el constructor inicializa la clase según lo previsto de este modo:

```cpp
        TEST_METHOD(TestClassInit)
        {
            std::string name = "Bill";
            MyClass mc(name);
            Assert::AreEqual(name, mc.GetName());
        }
```
En el ejemplo anterior, el resultado de la llamada `Assert::AreEqual` determina si la prueba se supera o no. La clase Assert contiene otros muchos métodos para comparar los resultados previstos con los reales.

Puede agregar *rasgos* para probar métodos para especificar los propietarios de la prueba, la prioridad y otro tipo de información. Así, podrá usar esos valores para ordenar y agrupar las pruebas en el **Explorador de pruebas**. Para obtener más información, consulte [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Ejecutar las pruebas

1. En el menú **Prueba**, elija **Windows** > **Explorador de pruebas**. En la siguiente ilustración se muestra un proyecto de prueba cuyas pruebas aún no se han ejecutado.

   ![Explorador de pruebas antes de ejecutar las pruebas](media/cpp-test-explorer.png)

   > [!NOTE]
   > La integración de CTest con el **Explorador de pruebas** aún no está disponible. Realice pruebas de CTest desde el menú principal de CMake.

1. Si ninguna de las pruebas está visible en la ventana, compile el proyecto de prueba haciendo clic con el botón derecho en el nodo correspondiente en el **Explorador de soluciones** y eligiendo **Compilar** o **Recompilar**.

1. En el Explorador de pruebas, elija **Ejecutar todas** o seleccione las pruebas concretas que quiera ejecutar. Haga clic con el botón derecho en una prueba para ver otras opciones, como la ejecución en modo de depuración con puntos de interrupción habilitados. Después de ejecutar todas las pruebas, la ventana muestra cuáles se han superado y cuáles no:

![Explorador de pruebas después de ejecutar las pruebas](media/cpp-test-explorer-passed.png)

En las pruebas no superadas, el mensaje ofrece detalles que ayudan a diagnosticar la causa. Puede hacer clic con el botón derecho en la prueba no superada y elegir **Depurar pruebas seleccionadas** para ir paso a paso por la función donde se ha producido el error.

Para más información sobre cómo usar el **Explorador de pruebas**, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md).

Para ver procedimientos recomendados relativos a las pruebas unitarias, vea [Conceptos básicos de prueba unitaria](unit-test-basics.md).

## <a name="see-also"></a>Vea también

[Haga una prueba unitaria de su código](unit-test-your-code.md)

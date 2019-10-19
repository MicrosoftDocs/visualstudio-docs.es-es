---
title: Pruebas unitarias de un archivo DLL de Visual C++ para una aplicación de la Tienda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d5f86eb40e1401f98a4c66d0b971fb006762cc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659691"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Pruebas unitarias de un archivo DLL de Visual C++ para una aplicación de la Tienda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tema describe una manera de crear pruebas unitarias para una DLL de C++ para las aplicaciones de la Tienda Windows. La DLL RooterLib muestra las memorias imprecisas de teoría límite desde el cálculo implementando una función que calcula una estimación de la raíz cuadrada de un número determinado. Más adelante, el archivo DLL se podría incluir en una aplicación de la Tienda Windows que muestre a los usuarios cosas interesantes que se pueden hacer con las matemáticas.

 En este tema se muestra cómo usar las pruebas unitarias como el primer paso del desarrollo. En este enfoque, primero tienes que escribir un método de prueba que compruebe un comportamiento concreto en el sistema que estés probando y, después, escribir el código que tenga que superar la prueba. Mediante la realización de cambios en el orden de los procedimientos siguientes, puedes invertir esta estrategia para escribir primero el código que deseas probar y escribe después las pruebas unitarias.

 En este tema también se crea una solución única de Visual Studio y proyectos independientes para las pruebas unitarias y el DLL que desees probar. También puede incluir las pruebas unitarias directamente en el proyecto DLL o puede crear soluciones independientes para las pruebas unitarias y el archivo .DLL. Consulte [Agregar pruebas unitarias a aplicaciones C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) para obtener sugerencias sobre qué estructura usar.

## <a name="BKMK_In_this_topic"></a> En este tema
 Este tema le indicará cómo realizar las siguientes tareas:

 [Crear la solución y el proyecto de prueba unitaria](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Comprobar que las pruebas se ejecutan en el Explorador de pruebas](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Agregar el proyecto DLL a la solución](#BKMK_Add_the_DLL_project_to_the_solution)

 [Acoplar el proyecto de prueba al proyecto DLL](#BKMK_Couple_the_test_project_to_the_dll_project)

 [Aumentar las pruebas de forma interactiva y comprobar si se superan](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Depurar una prueba fallida](#BKMK_Debug_a_failing_test)

 [Refactorizar el código sin cambiar las pruebas](#BKMK_Refactor_the_code_without_changing_tests)

## <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Crear la solución y el proyecto de prueba unitaria

1. En el menú **Archivo**, elija **Nuevo** y después **Nuevo proyecto**.

2. En el diálogo Nuevo proyecto, expanda **Instalado**, expanda **Visual C++** y elija **Windows Store**. Después elija **Biblioteca de pruebas unitarias (aplicaciones de la Tienda Windows)** en la lista de plantillas de proyecto.

     ![Crear una biblioteca&#43; &#43; de pruebas unitarias de C](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")

3. Asigne al proyecto el nombre `RooterLibTests`, especifique la ubicación, asigne a la solución el nombre `RooterLib` y asegúrese de que esté activada la opción **Crear directorio para la solución**.

     ![Especificar la solución y el nombre y la ubicación del proyecto](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")

4. En el nuevo proyecto, abra **unittest1.cpp**.

     ![UnitTest1. cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")

     Tenga en cuenta lo siguiente:

    - Cada prueba se define mediante `TEST_METHOD(YourTestName){...}`.

         No es necesario escribir una firma de función convencional. La firma se crea mediante la macro TEST_METHOD. La macro genera una función de la instancia que devuelve void. También genera una función estática que devuelve información sobre el método de prueba. Esta información permite al Explorador de pruebas encontrar el método.

    - Los métodos de prueba se agrupan en clases mediante el uso de `TEST_CLASS(YourClassName){...}`.

         Cuando se ejecutan las pruebas, se crea una instancia de cada clase de prueba. Se llama a los métodos de prueba en un orden no especificado. Puede definir métodos especiales que se invocan antes y después de cada módulo, clase o método. Para obtener más información, consulte [Usar Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) en MSDN Library.

## <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Compruebe que las pruebas se ejecutan en el Explorador de pruebas

1. Inserte código de prueba:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Tenga en cuenta que la clase `Assert` proporciona varios métodos estáticos que puede usar para comprobar los resultados de los métodos de prueba.

2. En el menú **Prueba**, elija **Ejecutar** y después **Ejecutar todas**.

     El proyecto de prueba se compila y ejecuta. Aparece la ventana Explorador de pruebas y la prueba se muestra debajo de **Pruebas superadas**. El panel Resumen de la parte inferior de la ventana proporciona detalles adicionales sobre la prueba seleccionada.

     ![Explorador de pruebas](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Agregar el proyecto DLL a la solución

1. En el Explorador de soluciones, elija el nombre de la solución. En el menú contextual, elija **Agregar** y después **Agregar nuevo proyecto**.

     ![Crear el proyecto RooterLib](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")

2. En el cuadro de diálogo **Agregar nuevo proyecto**, elija **DLL (aplicaciones de la Tienda Windows)** .

3. Agregue el siguiente código al archivo **RooterLib.h**:

    ```cpp
    // The following ifdef block is the standard way of creating macros which make exporting
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS
    // symbol defined on the command line. This symbol should not be defined on any project
    // that uses this DLL. This way any other project whose source files include this file see
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols
    // defined with this macro as being exported.
    #ifdef ROOTERLIB_EXPORTS
    #define ROOTERLIB_API  __declspec(dllexport)
    #else
    #define ROOTERLIB_API __declspec(dllimport)
    #endif //ROOTERLIB_EXPORTS

    class ROOTERLIB_API CRooterLib {
    public:
        CRooterLib(void);
        double SquareRoot(double v);
    };
    ```

     Los comentarios explican el bloque ifdef no solo para el desarrollador de la DLL, sino también para cualquier persona que haga referencia a la DLL en su proyecto. Puede agregar el símbolo ROOTERLIB_EXPORTS a la línea de comandos mediante las propiedades del proyecto del archivo DLL.

     La clase `CRooterLib` declara un constructor y el método de perito de `SqareRoot`.

4. Agregue el símbolo ROOTERLIB_EXPORTS a la línea de comandos.

    1. En el Explorador de soluciones, seleccione el proyecto **RooterLib** y elija **Propiedades** en el menú contextual.

         ![Agregar una definición de símbolo de preprocesador](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")

    2. En el cuadro de diálogo Página de propiedades de RooterLib, expanda **Propiedades de configuración**, después expanda **C++** y seleccione **Preprocesador**.

    3. Seleccione **\<Editar...>** en la lista **Definiciones de preprocesador** y agregue `ROOTERLIB_EXPORTS` en el cuadro de diálogo Definiciones de preprocesador.

5. Agregue las implementaciones mínimas de las funciones declaradas. Abra **RooterLib.cpp** y agregue el siguiente código:

    ```
    // constructor
    CRooterLib::CRooterLib()
    {
    }

    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        return 0.0;
    }

    ```

## <a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> Acoplar el proyecto de prueba al proyecto DLL

1. Agregue RooterLib al proyecto RooterLibTests.

   1. En el Explorador de soluciones, seleccione el proyecto **RooterLibTests** y elija **Referencias...** en el menú contextual.

   2. En el cuadro de diálogo Propiedades del proyecto RooterLib, expanda **Propiedades comunes** y elija **Marco de trabajo y referencias**.

   3. Elija **Agregar nueva referencia....**

   4. En el cuadro de diálogo **Agregar referencia**, expanda **Solución** y seleccione **Proyectos**. Después, seleccione el elemento **RouterLib**.

2. Incluya el archivo de encabezado RooterLib en **unittest1.cpp**.

   1. Abra **unittest1.cpp**.

   2. Agregue este código debajo de la línea `#include "CppUnitTest.h"`:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Agregue una prueba que use la función importada. Agregue el siguiente código a **unittest1.cpp**:

   ```
   TEST_METHOD(BasicTest)
   {
       CRooterLib rooter;
       Assert::AreEqual(
           // Expected value:
           0.0,
           // Actual value:
           rooter.SquareRoot(0.0),
           // Tolerance:
           0.01,
           // Message:
           L"Basic test failed",
           // Line number - used if there is no PDB file:
           LINE_INFO());
   }

   ```

4. Compile la solución.

    La nueva prueba aparece en el Explorador de pruebas en el nodo **Pruebas no ejecutadas**.

5. En el Explorador de pruebas, elija **Ejecutar todas**.

    ![Prueba básica superada](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Ha configurado la prueba y los proyectos de código, y ha verificado que puede ejecutar las pruebas que ejecutan funciones en el proyecto de código. Ahora puede empezar a escribir pruebas y código reales.

## <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Aumentar las pruebas de forma interactiva y comprobar si se superan

1. Agregue una nueva prueba:

    ```
    TEST_METHOD(RangeTest)
    {
        CRooterLib rooter;
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = expected/1000;
            Assert::AreEqual(expected, actual, tolerance);
        }
    };

    ```

    > [!TIP]
    > Se recomienda no cambiar las pruebas superadas. En vez de ello, agregue una nueva prueba, actualice el código para que la prueba se supere, después agregue otra prueba y así sucesivamente.
    >
    >  Cuando los usuarios cambien los requisitos, deshabilite las pruebas que ya no son correctas. Escriba nuevas pruebas y hágalas funcionar una a una de la misma manera incremental.

2. En el Explorador de pruebas, elija **Ejecutar todas**.

3. La prueba sufre un error.

     ![Error de RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Compruebe que todas las pruebas producen un error inmediatamente después de escribirlas. Esto ayuda a evitar el error habitual de escribir una prueba que nunca falla.

4. Mejora el código objeto de prueba para que la nueva prueba se supere. Agregue lo siguiente a **RooterLib.cpp**:

    ```cpp
    #include <math.h>
    ...
    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        double result = v;
        double diff = v;
        while (diff > result/1000)
        {
            double oldResult = result;
            result = result - (result*result - v)/(2*result);
            diff = abs (oldResult - result);
        }
        return result;
    }

    ```

5. Compile la solución y, en el Explorador de pruebas, elija **Ejecutar todo**.

     Ambas pruebas quedan superadas.

> [!TIP]
> Desarrolle código agregando pruebas una a una. Asegúrese de que se pasan todas las pruebas después de cada iteración.

## <a name="BKMK_Debug_a_failing_test"></a> Depurar una prueba fallida

1. Agregue otra prueba a **unittest1.cpp**:

   ```
   // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRooterLib rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          swprintf_s(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          swprintf_s(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
   };

   ```

2. En el Explorador de pruebas, elija **Ejecutar todas**.

    La prueba sufre un error. Elige el nombre de la prueba en el Explorador de pruebas. Se resalta el error de aserción. El mensaje de error es visible en el panel de detalles del Explorador de pruebas.

    ![Error de las pruebas negativerangetests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Para ver por qué se produce el error, revise la función:

   1. Establece un punto de interrupción al principio de la función `SquareRoot`.

   2. En el menú contextual de la prueba no superada, elija **Depurar pruebas seleccionadas**.

        Cuando la ejecución se detiene en el punto de interrupción, revise paso a paso el código.

   3. Agregue código a **RooterLib.cpp** para capturar la excepción:

       ```
       #include <stdexcept>
       ...
       double CRooterLib::SquareRoot(double v)
       {
           //Validate the input parameter:
           if (v < 0.0)
           {
             throw std::out_of_range("Can't do square roots of negatives");
           }
       ...

       ```

   1. En el Explorador de pruebas, elija **Ejecutar todas** para probar el método corregido y asegúrese de que no se haya introducido una regresión.

   Ahora, todas las pruebas pasan.

   ![Todas las pruebas se superan](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="BKMK_Refactor_the_code_without_changing_tests"></a> Refactorizar el código sin cambiar las pruebas

1. Simplifique el cálculo central de la función `SquareRoot`:

    ```
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Elija **Ejecutar todas** para probar el método refactorizado y asegúrese de que no haya introducido una regresión.

    > [!TIP]
    > Un conjunto estable de pruebas unitarias correctas proporciona la confianza de que no se han introducido errores al cambiar el código.
    >
    >  Mantenga la refactorización separada de los demás cambios.

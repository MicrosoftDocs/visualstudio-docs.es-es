---
title: Escribir pruebas unitarias para C/C++ con el Framework de pruebas unitarias de Microsoft para C++ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: gewarren
manager: douge
ms.openlocfilehash: d4e5da38500e5fd35fb14e1854fe1fa378a8553c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579505"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>Escribir pruebas unitarias para C/C++ con el Framework de pruebas unitarias de Microsoft para C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [escribir pruebas unitarias para C/C ++ con el marco de pruebas unitarias de Microsoft para C++](https://docs.microsoft.com/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp).  
  
En Visual Studio puede crear pruebas unitarias para código no administrado escrito en C++. El código no administrado se denomina a veces código nativo.  
  
 El siguiente procedimiento contiene la información esencial para empezar. Las secciones posteriores proporcionan un tutorial que describe los pasos más detalladamente.  
  
### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Escribir pruebas unitarias para un archivo DLL de código no administrado  
  
1.  Utilice la plantilla **Proyecto de prueba nativo** para crear un proyecto de Visual Studio independiente para las pruebas.  
  
     El proyecto contiene ejemplos de código de prueba.  
  
2.  Haga que el archivo DLL esté accesible para el proyecto de prueba:  
  
    -   Use `#include` para agregar un archivo `.h` que contiene declaraciones de las funciones del archivo DLL accesibles externamente.  
  
         El archivo `.h` debería contener declaraciones de función marcadas con `_declspec(dllimport)`. Como alternativa, puede exportar los métodos mediante un archivo DEF. Para obtener más información, consulte [Importar y exportar](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).  
  
         Las pruebas unitarias pueden acceder solo a las funciones que se exportan desde la DLL de prueba.  
  
    -   Agregue el proyecto DLL a las referencias del proyecto de prueba:  
  
         En las **Propiedades** del proyecto de prueba, expanda **Propiedades comunes**, **Framework y Referencias**y elija **Agregar referencia**.  
  
3.  En el proyecto de prueba, cree las clases y métodos de prueba mediante las macros de prueba y la clase Assert de la siguiente manera:  
  
    ```cpp  
    #include "stdafx.h"  
    #include <CppUnitTest.h>  
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    TEST_CLASS(TestClassName)  
    {  
    public:  
      TEST_METHOD(TestMethodName)  
      {  
        // Run a function under test here.  
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());  
      }  
    }  
    ```  
  
    -   `Assert` contiene diversas funciones estáticas que puede usar para comprobar el resultado de una prueba.  
  
    -   El parámetro `LINE_INFO()` es opcional. En los casos donde no hay ningún archivo PDB, permite al ejecutor de pruebas identificar la ubicación de un error.  
  
    -   También puede escribir métodos de instalación y limpieza de prueba. Para obtener más información, abra la definición de la macro `TEST_METHOD` y lea los comentarios sobre CppUnitTest.h  
  
    -   No se pueden anidar las clases de prueba.  
  
4.  Utilice el Explorador de pruebas para ejecutar las pruebas:  
  
    1.  En el menú **Ver** , elija **Otras ventanas**, **Explorador de pruebas**.  
  
    2.  Compile la solución de Visual Studio.  
  
    3.  En el Explorador de pruebas, elija **Ejecutar todas**.  
  
    4.  Para investigar cualquier prueba con más detalle en el Explorador de pruebas:  
  
        1.  Seleccione el nombre de la prueba para ver más detalles, como mensajes de error y el seguimiento de pila.  
  
        2.  Abra el nombre de la prueba (por ejemplo, haciendo doble clic) para ir a la ubicación del error o al código de prueba.  
  
        3.  En el menú contextual para una prueba, elija **Depurar prueba seleccionada** para ejecutar la prueba en el depurador.  
  
##  <a name="walkthrough"></a> Tutorial: Desarrollar una DLL no administrada con el Explorador de pruebas  
 Puede adaptar este tutorial para desarrollar su propio archivo DLL. Los principales pasos son los siguientes:  
  
1.  [Crear un proyecto de prueba nativo](#unitTestProject). Las pruebas se crean en un proyecto independiente del archivo DLL que se está desarrollando.  
  
2.  [Crear un proyecto DLL](#createDllProject). Este tutorial crea un nuevo archivo DLL, pero el procedimiento para probar una DLL existente es similar.  
  
3.  [Hacer visibles para las pruebas las funciones DLL](#coupleProjects).  
  
4.  [Aumentar de forma iterativa las pruebas](#iterate). Recomendamos un ciclo "rojo-verde-refactorizar" en el que el desarrollo del código lo dirigen las pruebas.  
  
5.  [Depurar errores de las pruebas](#debug). Puede ejecutar pruebas en modo de depuración.  
  
6.  [Refactorizar mientras mantiene las pruebas sin cambios](#refactor). Refactorizar significa mejorar la estructura del código sin cambiar su comportamiento externo. Puede hacerlo para mejorar el rendimiento, la extensibilidad o la legibilidad del código. Dado que la intención es no cambiar el comportamiento, no cambie las pruebas al realizar un cambio de refactorización en el código. Las pruebas le permiten asegurarse de que no crea nuevos errores mientras realiza la tarea de refactorizar. Por lo tanto, puede realizar estos cambios con mucha más confianza que si no tuviera las pruebas.  
  
7.  [Comprobar cobertura](https://msdn.microsoft.com/library/fc8hec9e.aspx). Las pruebas unitarias son más útiles cuanto más código ponen a prueba. Puede detectar qué partes del código han utilizado las pruebas.  
  
8.  [Aislar las unidades de los recursos externos](https://msdn.microsoft.com/library/hh549174.aspx). Normalmente, un archivo DLL depende de otros componentes del sistema que está desarrollando, como otros archivos DLL, bases de datos o subsistemas remotos. Es útil probar cada unidad aislada de sus dependencias. Los componentes externos pueden ralentizar las pruebas. Durante el desarrollo, los demás componentes podrían no estar completos.  
  
###  <a name="unitTestProject"></a> Crear un proyecto de prueba unitaria nativo  
  
1.  En el menú **Archivo** , elija **Nuevo**, **Proyecto**.  
  
     En el cuadro de diálogo, expanda **Instalado**, **Plantillas**, **Visual C++** y **Prueba**.  
  
     Elija la plantilla **Proyecto de prueba nativo** .  
  
     En este tutorial, el proyecto de prueba se llama `NativeRooterTest`.  
  
     ![Creación de un proyecto de prueba unitaria de C++](../test/media/utecpp01.png "UteCpp01")  
  
2.  En el nuevo proyecto, inspeccione **unittest1.cpp**.  
  
     ![Proyecto de prueba con TEST_CLASS y TEST_METHOD](../test/media/utecpp2.png "UteCpp2")  
  
     Tenga en cuenta que:  
  
    -   Cada prueba se define mediante `TEST_METHOD(YourTestName){...}`.  
  
         No es necesario escribir una firma de función convencional. La firma se crea mediante la macro TEST_METHOD. La macro genera una función de la instancia que devuelve void. También genera una función estática que devuelve información sobre el método de prueba. Esta información permite al Explorador de pruebas encontrar el método.  
  
    -   Los métodos de prueba se agrupan en clases mediante el uso de `TEST_CLASS(YourClassName){...}`.  
  
         Cuando se ejecutan las pruebas, se crea una instancia de cada clase de prueba. Se llama a los métodos de prueba en un orden no especificado. Puede definir métodos especiales que se invocan antes y después de cada módulo, clase o método.  
  
3.  Compruebe que las pruebas se ejecutan en el Explorador de pruebas:  
  
    1.  Inserte código de prueba:  
  
        ```cpp  
        TEST_METHOD(TestMethod1)  
        {  
        Assert::AreEqual(1,1);  
        }  
        ```  
  
         Tenga en cuenta que la clase `Assert` proporciona varios métodos estáticos que puede usar para comprobar los resultados de los métodos de prueba.  
  
    2.  En el menú **Prueba** , elija **Ejecutar** , **Todas las pruebas**.  
  
         La prueba se compila y ejecuta.  
  
         Aparece el Explorador de pruebas.  
  
         La prueba aparece en **Pruebas superadas**.  
  
         ![Explorador de pruebas unitarias con una prueba superada](../test/media/utecpp04.png "UteCpp04")  
  
###  <a name="createDllProject"></a> Crear un proyecto de DLL no administrado  
  
1.  Cree un proyecto de **Visual C++** usando la plantilla **Proyecto Win32** .  
  
     En este tutorial, el proyecto se llama `RootFinder`.  
  
     ![Creación de un proyecto Win32 de C++](../test/media/utecpp05.png "UteCpp05")  
  
2.  Seleccione **DLL** y **Exportar símbolos** en el asistente para aplicaciones Win32.  
  
     La opción **Exportar símbolos** genera una cómoda macro que puede utilizar para declarar métodos exportados.  
  
     ![Asistente para proyectos de C++ con las opciones de DLL y de exportar símbolos](../test/media/utecpp06.png "UteCpp06")  
  
3.  Declare una función exportada en el archivo .h principal:  
  
     ![Nuevo proyecto de código DLL y archivo .h con macros de API](../test/media/utecpp07.png "UteCpp07")  
  
     El declarador `__declspec(dllexport)` hace que los miembros públicos y protegidos de la clase sean visibles fuera del archivo DLL. Para obtener más información, consulta [Using dllimport and dllexport in C++ Classes](http://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).  
  
4.  En el archivo .cpp principal, agregue un cuerpo mínimo para la función:  
  
    ```cpp  
    // Find the square root of a number.  
    double CRootFinder::SquareRoot(double v)  
    {  
      return 0.0;  
    }  
    ```  
  
###  <a name="coupleProjects"></a> Acoplar el proyecto de prueba al proyecto DLL  
  
1.  Agregue el proyecto DLL a las referencias del proyecto de prueba:  
  
    1.  Abra las propiedades del proyecto de prueba y elija **Propiedades comunes**, **Framework y Referencias**.  
  
         ![Propiedades del proyecto de C++: marco de trabajo y referencias](../test/media/utecpp08.png "UteCpp08")  
  
    2.  Elija **Agregar nueva referencia**.  
  
         En el cuadro de diálogo **Agregar referencia** , seleccione el proyecto DLL y elija **Agregar**.  
  
         ![Propiedades del proyecto de C++: agregar nueva referencia](../test/media/utecpp09.png "UteCpp09")  
  
2.  En el archivo .cpp de prueba unitaria principal, incluya el archivo .h del código DLL:  
  
    ```cpp  
    #include "..\RootFinder\RootFinder.h"  
    ```  
  
3.  Agregue una prueba básica que utiliza la función exportada:  
  
    ```cpp  
    TEST_METHOD(BasicTest)  
    {  
    CRootFinder rooter;  
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
  
4.  Compile la solución.  
  
     La nueva prueba aparece en el Explorador de pruebas.  
  
5.  En el Explorador de pruebas, elija **Ejecutar todas**.  
  
     ![Explorador de pruebas unitarias: prueba básica superada](../test/media/utecpp10.png "UteCpp10")  
  
 Ha configurado la prueba y los proyectos de código, y ha verificado que puede ejecutar las pruebas que ejecutan funciones en el proyecto de código. Ahora puede empezar a escribir pruebas y código reales.  
  
###  <a name="iterate"></a> Aumentar las pruebas de forma interactiva y comprobar si se superan  
  
1.  Agregue una nueva prueba:  
  
    ```cpp  
    TEST_METHOD(RangeTest)  
    {  
      CRootFinder rooter;  
      for (double v = 1e-6; v < 1e6; v = v * 3.2)  
      {  
        double actual = rooter.SquareRoot(v*v);  
        Assert::AreEqual(v, actual, v/1000);  
      }  
    }  
    ```  
  
    > [!TIP]
    >  Se recomienda no cambiar las pruebas superadas. En vez de ello, agregue una nueva prueba, actualice el código para que la prueba se supere, después agregue otra prueba y así sucesivamente.  
    >   
    >  Cuando los usuarios cambien los requisitos, deshabilite las pruebas que ya no son correctas. Escriba nuevas pruebas y hágalas funcionar una a una de la misma manera incremental.  
  
2.  Compile la solución y, en el Explorador de pruebas, elija **Ejecutar todo**.  
  
     Se produce un error en la nueva prueba.  
  
     ![Se produce un error en RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Compruebe que todas las pruebas producen un error inmediatamente después de escribirlas. Esto ayuda a evitar el error habitual de escribir una prueba que nunca falla.  
  
3.  Mejore el código en pruebas de forma que supere la nueva prueba:  
  
    ```cpp  
    #include <math.h>  
    ...  
    double CRootFinder::SquareRoot(double v)  
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
  
4.  Compile la solución y, en el Explorador de pruebas, elija **Ejecutar todo**.  
  
     Ambas pruebas quedan superadas.  
  
     ![Explorador de pruebas unitarias: prueba de intervalo superada](../test/media/utecpp12.png "UteCpp12")  
  
    > [!TIP]
    >  Desarrolle código agregando pruebas una a una. Asegúrese de que se pasan todas las pruebas después de cada iteración.  
  
###  <a name="debug"></a> Depurar una prueba fallida  
  
1.  Agregue otra prueba:  
  
    ```cpp  
  
    #include <stdexcept>  
    ...  
    // Verify that negative inputs throw an exception.  
    TEST_METHOD(NegativeRangeTest)  
    {  
      wchar_t message[200];  
      CRootFinder rooter;  
      for (double v = -0.1; v > -3.0; v = v - 0.5)  
      {  
        try   
        {  
          // Should raise an exception:  
          double result = rooter.SquareRoot(v);  
  
          _swprintf(message, L"No exception for input %g", v);  
          Assert::Fail(message, LINE_INFO());  
        }  
        catch (std::out_of_range ex)  
        {  
          continue; // Correct exception.  
        }  
        catch (...)  
        {  
          _swprintf(message, L"Incorrect exception for %g", v);  
          Assert::Fail(message, LINE_INFO());  
        }  
      }  
    }  
    ```  
  
2.  Compile la solución y elija **Ejecutar todo**.  
  
3.  Abra o haga doble clic en la prueba con errores.  
  
     Se resalta el error de aserción. El mensaje de error es visible en el panel de detalles del Explorador de pruebas.  
  
     ![Error de NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
4.  Para ver por qué se produce el error, revise la función:  
  
    1.  Establezca un punto de interrupción al principio de la función SquareRoot.  
  
    2.  En el menú contextual de la prueba no superada, elija **Depurar pruebas seleccionadas**.  
  
         Cuando la ejecución se detiene en el punto de interrupción, revise paso a paso el código.  
  
5.  Inserte código en la función que está desarrollando:  
  
    ```cpp  
  
    #include <stdexcept>  
    ...  
    double CRootFinder::SquareRoot(double v)  
    {  
        // Validate parameter:  
        if (v < 0.0)   
        {  
          throw std::out_of_range("Can't do square roots of negatives");  
        }  
  
    ```  
  
6.  Ahora, todas las pruebas pasan.  
  
     ![Todas las pruebas pasan](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
> [!TIP]
>  Si las pruebas individuales no tienen ninguna dependencia que impida que se ejecuten en cualquier orden, active la ejecución de pruebas paralelas con el botón de alternancia ![UTE&#95;parallelicon&#45;small](../test/media/ute-parallelicon-small.png "UTE_parallelicon-small") en la barra de herramientas. Esto puede reducir considerablemente el tiempo necesario para ejecutar todas las pruebas.  
  
###  <a name="refactor"></a> Refactorizar el código sin cambiar las pruebas  
  
1.  Simplifique el cálculo central en la función SquareRoot:  
  
    ```  
    // old code:  
    //   result = result - (result*result - v)/(2*result);  
    // new code:  
         result = (result + v/result)/2.0;  
  
    ```  
  
2.  Compile la solución y elija **Ejecutar todo**para asegurarse de que no se ha introducido un error.  
  
    > [!TIP]
    >  Un buen conjunto de pruebas unitarias le da la seguridad de que no ha introducido errores al cambiar el código.  
    >   
    >  Mantenga la refactorización separada de los demás cambios.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   **Aislamiento.** La mayoría de las DLL dependen de otros subsistemas, como bases de datos y otros archivos DLL. Estos componentes a menudo se desarrollan en paralelo. Para permitir la realización de pruebas unitarias mientras los demás componentes no están disponibles, debe sustituir mock o  
  
-   **Pruebas de comprobación de la compilación.** Puede realizar pruebas en el servidor de compilación de su equipo a intervalos establecidos. Esto garantiza que no se producen errores cuando se integra el trabajo de varios miembros del equipo.  
  
-   **Pruebas de protección.** Puede exigir que se realicen algunas pruebas antes de que cualquier miembro del equipo proteja código en el control de código fuente. Normalmente, se trata de un subconjunto de las pruebas de comprobación.  
  
     También puede asignar un nivel mínimo de cobertura de código.  
  
## <a name="see-also"></a>Vea también  
 [Agregar pruebas unitarias a aplicaciones C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)   
 [Usar Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)   
 [Información general sobre la interoperabilidad de código administrado y no administrado](http://msdn.microsoft.com/library/ms973872.aspx)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Tutorial: Crear y utilizar una biblioteca de vínculos dinámicos (C++)](http://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941)   
 [Importar y exportar](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)




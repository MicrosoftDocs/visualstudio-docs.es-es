---
title: "Cómo usar Boost.Test para C++ en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdf772be03f6021f499b9bf777922d6d2743e0dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Cómo usar Boost.Test para C++ en Visual Studio

En la **versión 15.5 de Visual Studio 2017** y en las versiones posteriores, el adaptador de prueba Boost.Test se integra en el IDE de Visual Studio como componente de la carga de trabajo **Desarrollo para el escritorio con C++**.

![Test Adapter para Boost.Test](media/cpp-boost-component.png "Componente de Test Adapter para Boost.Test")

Si no tiene instalada la carga de trabajo **Desarrollo para el escritorio con C++**, abra el **Instalador de Visual Studio** y seleccione **Modificar**. Seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y, luego, elija el botón **Modificar**.

## <a name="install-boost"></a>Instalar Boost

Boost.Test requiere [Boost](http://www.boost.org/)! Si no tiene Boost instalado, se recomienda que use el administrador de paquetes de Vcpkg.

1. Siga las instrucciones de [Vcpkg: Administrador de paquetes de C++ para Windows](/cpp/vcpkg) para instalar vcpkg (si aún no lo tiene).

1. Instale la biblioteca dinámica o estática Boost.Test:

    - Ejecute `vcpkg install boost-test` para instalar la biblioteca dinámica Boost.Test.
    
       O BIEN
       
    - Ejecute `vcpkg install boost-test:x86-windows-static` para instalar la biblioteca estática Boost.Test.

1. Ejecute `vcpkg integrate install` para configurar Visual Studio con la biblioteca e incluir rutas de acceso a los archivos de encabezado y binarios de Boost.

## <a name="create-a-project-for-your-tests"></a>Crear un proyecto para las pruebas

> [!NOTE]
> En la versión 15.5 de Visual Studio 2017, no hay disponible ninguna plantilla de proyecto o de elemento de prueba preconfigurada para Boost.Test. Por lo tanto, tendrá que crear un proyecto de aplicación de consola que contenga las pruebas. Está previsto que en una versión futura de Visual Studio haya plantillas de prueba para Boost.Test.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar** > **Nuevo proyecto...**

1. En el panel izquierdo, elija **Visual C++** > **Escritorio de Windows** y, después, elija la plantilla **Aplicación de consola Windows**.

1. Asigne un nombre al proyecto y elija **Aceptar**.

## <a name="link-and-configuration-boost-static-library-only"></a>Vínculo y configuración (solo para la biblioteca estática Boost)

Configure el proyecto para ejecutar las pruebas de Boost.Test.

1. Para editar el archivo de proyecto, primero descárguelo. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y elija **Descargar proyecto**. Después, haga clic con el botón derecho en el nodo del proyecto y elija **Editar <name\>.vcxproj**.

1. Agregue dos líneas al grupo de propiedades **Globales**, tal y como se muestra aquí:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. Guarde y cierre el archivo \*.vcxproj y, luego, vuelva a cargar el proyecto.

1. Para abrir **Páginas de propiedades**, haga clic con el botón derecho en el nodo del proyecto y elija **Propiedades**.

1. Expanda **C/C++** > **Generación de código** y, después, seleccione **Biblioteca en tiempo de ejecución**. Seleccione `/MTd` para la biblioteca en tiempo de ejecución estática de depuración y `/MT` para la biblioteca en tiempo de ejecución estática de versión.

1. Expanda **Enlazador > Sistema**. Compruebe que **SubSystem** esté establecido como **Consola**.

1. Haga clic en **Aceptar** para cerrar las páginas de propiedades.

## <a name="add-include-directives"></a>Agregar directivas include

1. Si hay una función `main` en su archivo de prueba .cpp, elimínela.

1. En el archivo .cpp de prueba, agregue las directivas `#include` que sean necesarias para que los tipos y funciones del programa estén visibles en el código de prueba. El programa suele estar un nivel por encima en la jerarquía de carpetas. Si escribe `#include "../"`, aparecerá una ventana de IntelliSense en la que podrá seleccionar la ruta de acceso completa al archivo de encabezado.

   ![Agregar directivas #include](media/cpp-gtest-includes.png "Agregar directivas #include al archivo .cpp de prueba")

   Puede usar la biblioteca independiente con lo siguiente:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   O bien, utilice la versión de encabezado único con lo siguiente:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Después, defina `BOOST_TEST_MODULE`.

El siguiente ejemplo es suficiente para que la prueba se pueda detectar en el **Explorador de pruebas**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Escribir y ejecutar pruebas
Ya está listo para escribir y ejecutar pruebas de Boost Test. Vea la [documentación de la biblioteca de Boost Test](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html) para más información sobre las macros de prueba. Vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) para más información sobre cómo detectar, ejecutar y agrupar las pruebas usando el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también
[Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

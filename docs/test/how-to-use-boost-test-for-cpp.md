---
title: Cómo usar Boost.Test para C++
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 47d88220af7d0e28c724cf5ec64eff729b2c35a0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008743"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Cómo usar Boost.Test para C++ en Visual Studio

En la **versión 15.5 de Visual Studio 2017** y en las versiones posteriores, el adaptador de prueba Boost.Test se integra en el IDE de Visual Studio como componente de la carga de trabajo **Desarrollo para el escritorio con C++**.

![Test Adapter para Boost.Test](media/cpp-boost-component.png)

Si no tiene instalada la carga de trabajo **Desarrollo para el escritorio con C++**, abra el **Instalador de Visual Studio** y seleccione **Modificar**. Seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y, luego, elija el botón **Modificar**.

## <a name="install-boost"></a>Instalar Boost

Boost.Test requiere [Boost](http://www.boost.org/)! Si no tiene Boost instalado, se recomienda que use el administrador de paquetes de Vcpkg.

1. Siga las instrucciones de [Vcpkg: Administrador de paquetes de C++ para Windows](/cpp/vcpkg) para instalar vcpkg (si aún no lo tiene).

1. Instale la biblioteca dinámica o estática Boost.Test:

    - Ejecute **vcpkg install boost-test** para instalar la biblioteca dinámica Boost.Test.

       O BIEN

    - Ejecute **vcpkg install boost-test:x86-windows-static** para instalar la biblioteca estática Boost.Test.

1. Ejecute **vcpkg integrate install** para configurar Visual Studio con la biblioteca e incluir rutas de acceso a los archivos de encabezado y binarios de Boost.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Incorporación de la plantilla de elemento (versión 15.6 y posteriores de Visual Studio 2017)

1. Para crear un archivo *.cpp* para las pruebas, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y elija **Agregar nuevo elemento**.

   ![Plantilla de elemento Boost.Test](media/boost_test_item_template.png)

1. El archivo nuevo contiene un método de prueba de ejemplo. Compile el proyecto para permitir que el **Explorador de pruebas** descubra el método.

La plantilla de elemento usa la variante de Boost.Test de un solo encabezado, pero puede modificar la ruta de acceso #include para usar la variante de biblioteca independiente. Para más información, consulte [Agregar directivas include](#add-include-directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Creación de un proyecto de prueba (versión 15.5 de Visual Studio 2017)

En la versión 15.5 de Visual Studio 2017, no hay disponible ninguna plantilla de proyecto o de elemento de prueba preconfigurada para Boost.Test. Por lo tanto, tendrá que crear y configurar un proyecto de aplicación de consola que contenga las pruebas.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar** > **Nuevo proyecto**.

1. En el panel izquierdo, elija **Visual C++** > **Escritorio de Windows** y, después, elija la plantilla **Aplicación de consola Windows**.

1. Asigne un nombre al proyecto y elija **Aceptar**.

1. Elimine la función `main` en el archivo *.cpp*.

1. Si usa la versión de biblioteca dinámica o de un solo encabezado de Boost.Test, vaya a [Agregar directivas include](#add-include-directives). Si usa la versión de biblioteca estática, debe llevar a cabo cierta configuración adicional:

   a. Para editar el archivo de proyecto, primero descárguelo. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y elija **Descargar proyecto**. Después, haga clic con el botón derecho en el nodo del proyecto y elija **Editar <name\>.vcxproj**.

   b. Agregue dos líneas al grupo de propiedades **Globales**, tal y como se muestra aquí:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c. Guarde y cierre el archivo *\*.vcxproj* y, luego, vuelva a cargar el proyecto.

   d. Para abrir **Páginas de propiedades**, haga clic con el botón derecho en el nodo del proyecto y elija **Propiedades**.

   d. Expanda **C/C++** > **Generación de código** y, después, seleccione **Biblioteca en tiempo de ejecución**. Seleccione **/MTd** para la biblioteca en tiempo de ejecución estática de depuración o **/MT** para la biblioteca en tiempo de ejecución estática de versión.

   f. Expanda **Enlazador** > **Sistema**. Compruebe que **SubSystem** esté establecido como **Consola**.

   g. Haga clic en **Aceptar** para cerrar las páginas de propiedades.

## <a name="add-include-directives"></a>Agregar directivas include

1. En el archivo *.cpp* de prueba, agregue las directivas `#include` que sean necesarias para que los tipos y funciones del programa estén visibles en el código de prueba. El programa suele estar un nivel por encima en la jerarquía de carpetas. Si escribe `#include "../"`, aparecerá una ventana de IntelliSense en la que podrá seleccionar la ruta de acceso completa al archivo de encabezado.

   ![Agregar directivas #include](media/cpp-gtest-includes.png)

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

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Escribir y ejecutar pruebas

Ya está listo para escribir y ejecutar pruebas de Boost Test. Vea la [documentación de la biblioteca de Boost Test](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html) para obtener más información sobre las macros de prueba. Vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) para más información sobre cómo detectar, ejecutar y agrupar las pruebas usando el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también

- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

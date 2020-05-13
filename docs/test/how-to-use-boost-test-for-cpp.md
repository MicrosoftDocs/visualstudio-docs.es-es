---
title: Cómo usar Boost.Test para C++
description: Use Boost.Test para crear pruebas unitarias en Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922921"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Cómo usar Boost.Test para C++ en Visual Studio

En Visual Studio 2017 y versiones posteriores, el adaptador de prueba Boost.Test se integra en el IDE de Visual Studio. Es un componente de la carga de trabajo **Desarrollo para el escritorio con C++** .

![Test Adapter para Boost.Test](media/cpp-boost-component.png)

Si no tiene instalada la carga de trabajo **Desarrollo para el escritorio con C++** , abra el **Instalador de Visual Studio**. Seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y, luego, elija el botón **Modificar**.

## <a name="install-boost"></a>Instalar Boost

Boost.Test requiere [Boost](https://www.boost.org/)! Si no tiene Boost instalado, se recomienda que use el administrador de paquetes Vcpkg.

1. Siga las instrucciones de [Vcpkg: Administrador de paquetes de C++ para Windows](/cpp/vcpkg) para instalar vcpkg (si aún no lo tiene).

1. Instale la biblioteca dinámica o estática Boost.Test:

    - Ejecute `vcpkg install boost-test` para instalar la biblioteca dinámica Boost.Test.

       O BIEN

    - Ejecute `vcpkg install boost-test:x86-windows-static` para instalar la biblioteca estática Boost.Test.

1. Ejecute `vcpkg integrate install` para configurar Visual Studio con la biblioteca e incluir rutas de acceso a los archivos de encabezado y binarios de Boost.

Tiene la opción de configurar las pruebas dentro de la solución en Visual Studio: Puede incluir el código de prueba en el proyecto en pruebas, o bien puede crear un proyecto de prueba independiente para las pruebas. Las dos opciones tienen ventajas y desventajas.

## <a name="add-tests-inside-your-project"></a>Adición de pruebas dentro del proyecto

En Visual Studio 2017, versión 15.6 y posteriores, puede agregar una plantilla de elementos para las pruebas en el proyecto. Tanto las pruebas como el código residen en el mismo proyecto. Tendrá que crear una configuración de compilación independiente para generar una compilación de prueba. Además, tendrá que mantener las pruebas fuera de las compilaciones de depuración y versión.

En la versión 15.5 de Visual Studio 2017, no hay disponible ninguna plantilla de proyecto o de elemento de prueba preconfigurada para Boost.Test. Siga las instrucciones para crear y configurar un proyecto de prueba independiente.

### <a name="create-a-boosttest-item"></a>Creación de un elemento Boost.Test

1. Para crear un archivo *.cpp* para las pruebas, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y elija **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, expanda **Instalado** > **Visual C++**  > **Prueba**. Seleccione **Boost.Test** y, después, elija **Agregar** para agregar *Test.cpp* al proyecto.

   ![Plantilla de elemento Boost.Test](media/boost_test_item_template.png)

El nuevo archivo *Test.cpp* contiene un método de prueba de ejemplo. En este archivo puede incluir archivos de encabezado propios y escribir pruebas para la aplicación.

En el archivo de prueba también se usan macros para definir una nueva rutina `main` para las configuraciones de prueba. Si compila el proyecto ahora, verá un error LNK2005, como "_main ya está definido en main.obj".

### <a name="create-and-update-build-configurations"></a>Creación y actualización de configuraciones de compilación

1. Para crear una configuración de prueba, en la barra de menús, seleccione **Compilar** > **Configuration Manager**. En el cuadro de diálogo **Configuration Manager**, abra la lista desplegable **Configuración de soluciones activas** y elija **Nueva**. En el cuadro de diálogo **Nueva configuración de la solución**, escriba un nombre como "Depuración de UnitTests". En **Copiar configuración de**, seleccione **Depuración** y, después, **Aceptar**.

1. Excluya el código de prueba de las configuraciones Debug y Release: En el **Explorador de soluciones**, haga clic con el botón derecho en Test.cpp y seleccione **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, seleccione **Todas las configuraciones** en la lista desplegable **Configuración**. Seleccione **Propiedades de configuración** > **General** y abra la lista desplegable de la propiedad **Excluir de la compilación**. Seleccione **Sí** y, después, **Aplicar** para guardar los cambios.

1. Para incluir el código de prueba en la configuración Depuración de UnitTests, en el cuadro de diálogo **Páginas de propiedades**, seleccione **Depuración de UnitTests**, en la lista desplegable **Configuración**. Seleccione **No** en la propiedad **Excluir de la compilación** y, después, seleccione **Aceptar** para guardar los cambios.

1. Excluya el código principal de la configuración de Depuración de UnitTests. En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo que contenga la función `main` y seleccione **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, seleccione **Depuración de UnitTests** en la lista desplegable **Configuración**. Seleccione **Propiedades de configuración** > **General** y abra la lista desplegable de la propiedad **Excluir de la compilación**. Seleccione **Sí** y, después, **Aceptar** para guardar los cambios.

1. Establezca Configuración de la solución en **Depuración de UnitTests** y, después, compile el proyecto para permitir que el **Explorador de pruebas** detecte el método.

Mientras que el nombre de configuración que cree empiece por las palabras "Debug" (Depuración) o "Release" (Versión), se seleccionarán de forma automática las bibliotecas de Boost.Test correspondientes.

La plantilla de elemento usa la variante de Boost.Test de un solo encabezado, pero puede modificar la ruta de acceso #include para usar la variante de biblioteca independiente. Para más información, consulte [Agregar directivas include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Creación de un proyecto de prueba independiente

En muchos casos, es más fácil usar un proyecto independiente para las pruebas. No tendrá que crear una configuración de prueba especial para el proyecto. Otra opción es excluir los archivos de prueba de las compilaciones de depuración y versión.

### <a name="to-create-a-separate-test-project"></a>Para crear un proyecto de prueba independiente

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar** > **Nuevo proyecto**.

1. En el cuadro de diálogo **Agregar un nuevo proyecto**, seleccione **C++** , **Windows** y **Consola** en las listas desplegables de filtros. Seleccione la plantilla **Aplicación de consola** y, después, **Siguiente**.

1. Asigne un nombre al proyecto y elija **Crear**.

1. Elimine la función `main` en el archivo *.cpp*.

1. Si va a usar la versión de biblioteca dinámica o de un solo encabezado de Boost.Test, vaya a [Agregar directivas include](#add-include-directives). Si va a usar la versión de biblioteca estática, tendrá que realizar una configuración adicional:

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

   e. Expanda **C/C++**  > **Generación de código** y, después, seleccione **Biblioteca en tiempo de ejecución**. Seleccione **/MTd** para la biblioteca en tiempo de ejecución estática de depuración o **/MT** para la biblioteca en tiempo de ejecución estática de versión.

   f. Expanda **Enlazador** > **Sistema**. Compruebe que **SubSystem** esté establecido como **Consola**.

   g. Haga clic en **Aceptar** para cerrar las páginas de propiedades.

## <a name="add-include-directives"></a>Agregar directivas include

1. En el archivo *.cpp* de prueba, agregue las directivas `#include` que sean necesarias para que los tipos y funciones del programa estén visibles en el código de prueba. Si va a usar un proyecto de prueba independiente, normalmente el programa se encuentra en un nivel relacionado de la jerarquía de carpetas. Si escribe `#include "../"`, aparecerá una ventana de IntelliSense en la que podrá seleccionar la ruta de acceso completa al archivo de encabezado.

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

Ya está listo para escribir y ejecutar pruebas de Boost Test. Vea la [documentación de la biblioteca de Boost Test](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) para obtener más información sobre las macros de prueba. Vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) para más información sobre cómo detectar, ejecutar y agrupar las pruebas usando el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también

- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

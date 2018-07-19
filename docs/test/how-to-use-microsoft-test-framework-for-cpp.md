---
title: Usar el marco de pruebas unitarias de Microsoft para C++ en Visual Studio
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 068e49c1fb095691cfa68f7a744a2159a8c173a3
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845498"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Usar el marco de pruebas unitarias de Microsoft para C++ en Visual Studio

El marco de pruebas unitarias de Microsoft para C++ se incluye de forma predeterminada en la carga de trabajo de **desarrollo para el escritorio con C++**.

##  <a name="separate_project"></a>Para escribir pruebas unitarias en un proyecto independiente
Normalmente, el código de prueba hay que ejecutarlo en su propio proyecto, en la misma solución que el código que quiere probar. Para instalar y configurar un nuevo proyecto de prueba, vea [Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md).

##  <a name="same_project"></a> Para escribir pruebas unitarias en el mismo proyecto
En algunos casos (por ejemplo, al probar funciones no exportadas en una DLL), puede que tenga que crear las pruebas en el mismo proyecto que el programa que quiere probar. Para escribir pruebas unitarias en el mismo proyecto:

1.  Modifique las propiedades del proyecto para incluir los encabezados y los archivos de biblioteca que sean necesarios para las pruebas unitarias.

    1.  En el Explorador de soluciones, haga clic con el botón derecho en el nodo de proyecto del programa que esté probando y, luego, elija **Propiedades | Propiedades de configuración | Directorios de VC++**.

    3.  Haga clic en la flecha abajo en las siguientes filas y elija **<Edit>**:

        |Directorio|Propiedad.|
        |-|-|
        |**Directorios de archivos de inclusión**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|
        |**Directorios de archivos de bibliotecas**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2.  Agregue el archivo de prueba unitaria de C++:

    -   Haga clic con el botón derecho en el nodo de proyecto en el **Explorador de soluciones** y elija **Agregar | Nuevo elemento | Prueba unitaria de C++**.

## <a name="write-the-tests"></a>Escribir las pruebas
Cualquier archivo .cpp con clases de prueba debe incluir "CppUnitTest.h" y tener una instrucción Using para `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. El proyecto de prueba ya está configurado. También incluye una definición de espacio de nombres y una TEST_CLASS con un TEST_METHOD para que pueda empezar. Puede cambiar el nombre del espacio de nombres, así como los nombres entre paréntesis de las macros de la clase y el método.

Se han definido macros especiales para inicializar los módulos, las clases y los métodos de prueba, así como para limpiar recursos cuando las pruebas se hayan completado. Estas macros generan código que se ejecuta antes de que se tenga acceso por primera vez a una clase o a un método y después de que se haya ejecutado la última prueba. Para más información, vea [Inicialización y limpieza](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Use los métodos estáticos de la clase [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) para definir las condiciones de la prueba. Use la clase [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) para escribir mensajes en la **Ventana de salida**. Agregar atributos a los métodos de prueba

## <a name="run-the-tests"></a>Ejecutar las pruebas

1.  En el menú **Prueba**, elija **Windows** y **Explorador de pruebas**.
2. Si ninguna de las pruebas está visible en la ventana, compile el proyecto de prueba haciendo clic con el botón derecho en el nodo correspondiente en el **Explorador de soluciones** y eligiendo **Compilar** o **Recompilar**.

2.  En el Explorador de pruebas, elija **Ejecutar todas** o seleccione las pruebas concretas que quiera ejecutar. Haga clic con el botón derecho en una prueba para ver otras opciones, como la ejecución en modo de depuración con puntos de interrupción habilitados.
3. En la **Ventana de salida**, seleccione **Pruebas** en la lista desplegable para ver los mensajes escritos por la clase `Logger`:

  ![Ventana de salida de C++ con mensajes de prueba](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definir rasgos para permitir la agrupación
Se pueden definir rasgos en los métodos de prueba para poder clasificar y agrupar las pruebas en el **Explorador de pruebas**. Para definir un rasgo, use la macro `TEST_METHOD_ATTRIBUTE` . Por ejemplo definir un rasgo denominado `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Para usar el rasgo definido en las pruebas unitarias:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Macros de atributo de rasgo de C++
  Encontrará los siguientes rasgos predefinidos en `CppUnitTest.h`. Para más información, vea la [referencia de API del marco de pruebas unitarias de Microsoft para C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Descripción|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Para definir un rasgo, use la macro TEST_METHOD_ATTRIBUTE.|
|`TEST_OWNER(ownerAlias)`|Para especificar un propietario del método de prueba, use el rasgo de propietario predefinido.|
|`TEST_PRIORITY(priority)`|Para asignar prioridades relativas a los métodos de prueba, use el rasgo de prioridad predefinido.|


## <a name="see-also"></a>Vea también
[Inicio rápido: Desarrollo controlado por pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md)


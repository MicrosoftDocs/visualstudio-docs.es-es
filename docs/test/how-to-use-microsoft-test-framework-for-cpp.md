---
title: Usar el marco de pruebas unitarias de Microsoft para C++
description: Use la plataforma de pruebas unitarias de Microsoft para C++ para crear pruebas unitarias para el código C++.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: 789430e18dfe8e5f7db19273e7298af2f078c0dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755569"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Usar el marco de pruebas unitarias de Microsoft para C++ en Visual Studio

El marco de pruebas unitarias de Microsoft para C++ se incluye de forma predeterminada en la carga de trabajo de **desarrollo para el escritorio con C++** .

## <a name="separate_project"></a>Para escribir pruebas unitarias en un proyecto independiente

Normalmente, el código de prueba hay que ejecutarlo en su propio proyecto, en la misma solución que el código que quiere probar. Para instalar y configurar un nuevo proyecto de prueba, vea [Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="same_project"></a> Para escribir pruebas unitarias en el mismo proyecto

En algunos casos (por ejemplo, al probar funciones no exportadas en una DLL), puede que tenga que crear las pruebas en el mismo proyecto que el programa que quiere probar. Para escribir pruebas unitarias en el mismo proyecto:

1. Modifique las propiedades del proyecto para incluir los encabezados y los archivos de biblioteca que sean necesarios para las pruebas unitarias.

   1. En el Explorador de soluciones, en el menú contextual del proyecto en pruebas, seleccione **Propiedades**. Se abrirá la ventana de propiedades del proyecto.

   1. En el cuadro de diálogo Páginas de propiedades, seleccione **Propiedades de configuración** > **Directorios de VC++** .

   1. Haga clic en la flecha abajo de las siguientes filas y seleccione **\<Editar>** . Agregue estas rutas de acceso:

      | Directorio | Propiedad. |
      |-| - |
      | **Directorios de archivos de inclusión** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **Directorios de archivos de bibliotecas** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Agregue el archivo de prueba unitaria de C++:

   - Haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo elemento** > **Archivo de C++ (.cpp)** .

## <a name="object_files"></a> Para vincular las pruebas a los archivos de biblioteca u objeto

Si el código en pruebas no exporta las funciones que quiere probar, puede agregar el archivo de salida **.obj** o **.lib** a las dependencias del proyecto de prueba. Modifique las propiedades del proyecto de prueba para incluir los encabezados y los archivos objeto o de biblioteca que sean necesarios para las pruebas unitarias.

1. En el Explorador de soluciones, en el menú contextual del proyecto de prueba, seleccione **Propiedades**. Se abrirá la ventana de propiedades del proyecto.

1. Seleccione la página **Propiedades de configuración** > **Enlazador** > **Entrada** y, a continuación, seleccione **Dependencias adicionales**.

   Seleccione **Editar** y agregue los nombres de los archivos **.obj** o **.lib**. No utilice nombres de ruta de acceso completa.

1. Seleccione la página **Propiedades de configuración** > **Enlazador** > **General** y, a continuación, seleccione **Directorios de bibliotecas adicionales**.

   Seleccione **Editar** y agregue la ruta del directorio de los archivos **.obj** o **.lib**. La ruta de acceso está normalmente dentro de la carpeta de compilación del proyecto en pruebas.

1. Seleccione la página **Propiedades de configuración** > **Directorios de VC++** y, a continuación, seleccione **Directorios de inclusión**.

   Elija **Editar** y agregue el directorio del encabezado del proyecto en pruebas.

## <a name="write-the-tests"></a>Escribir las pruebas

Cualquier archivo *.cpp* con clases de prueba debe incluir "CppUnitTest.h" y tener una instrucción Using para `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. El proyecto de prueba ya está configurado. También incluye una definición de espacio de nombres y una TEST_CLASS con un TEST_METHOD para que pueda empezar. Puede cambiar el nombre del espacio de nombres y los nombres entre paréntesis de las macros de la clase y el método.

La plataforma de prueba define macros especiales para inicializar los módulos, las clases y los métodos de prueba, así como para limpiar recursos después de que se completan las pruebas. Estas macros generan código para ejecutarse antes de que se tenga acceso por primera vez a una clase o a un método y después de que se haya ejecutado la última prueba. Para más información, vea [Inicialización y limpieza](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Use los métodos estáticos de la clase [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) para definir las condiciones de la prueba. Use la clase [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) para escribir mensajes en la **Ventana de salida**. Agregar atributos a los métodos de prueba

## <a name="run-the-tests"></a>Ejecutar las pruebas

1. En el menú **Prueba**, elija **Windows** > **Explorador de pruebas**.

1. Si no todas las pruebas son visibles en la ventana, compile el proyecto de prueba. Para ello, haga clic con el botón derecho en el nodo correspondiente del **Explorador de soluciones** y elija **Compilar** o **Recompilar**.

1. En el **Explorador de pruebas**, elija **Ejecutar todas** o seleccione las pruebas concretas que quiera ejecutar. Haga clic con el botón derecho en una prueba para ver otras opciones, como la ejecución en modo de depuración con puntos de interrupción habilitados.

1. En la **Ventana de salida**, elija **Pruebas** en la lista desplegable para ver los mensajes escritos por la clase `Logger`:

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

Encontrará los siguientes rasgos predefinidos en `CppUnitTest.h`. Para obtener más información, vea la [referencia de API del marco de pruebas unitarias de Microsoft para C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Macro|Descripción|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Para definir un rasgo, use la macro TEST_METHOD_ATTRIBUTE.|
|`TEST_OWNER(ownerAlias)`|Para especificar un propietario del método de prueba, use el rasgo de propietario predefinido.|
|`TEST_PRIORITY(priority)`|Para asignar prioridades relativas a los métodos de prueba, use el rasgo de prioridad predefinido.|

## <a name="see-also"></a>Vea también

- [Inicio rápido: Desarrollo controlado por pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md)

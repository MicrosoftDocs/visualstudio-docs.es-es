---
title: Escritura de pruebas unitarias para archivos DLL de C++
description: Obtenga información sobre las diversas maneras de probar código de DLL, dependiendo de si el archivo DLL exporta las funciones que quiere probar.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: b7eb7b7be524e20ca87c70c3f1f771f4f8a01141
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328631"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Escribir pruebas unitarias para DLL de C/C++ en Visual Studio

Hay varias maneras de probar código de DLL, dependiendo de si dicho código exporta las funciones que quiere probar. Elija una de las siguientes formas:

**Las pruebas unitarias solo llaman a funciones que se exportan desde la DLL:** agregue un proyecto de prueba independiente, como se describe en [Escribir pruebas unitarias para C/C ++](writing-unit-tests-for-c-cpp.md). En el proyecto de prueba, agregue una referencia al proyecto DLL.

Vaya al procedimiento [Para hacer referencia a funciones exportadas del proyecto DLL](#projectRef).

**La DLL se compila como un archivo .exe:** agregue un proyecto de prueba independiente. Vincúlelo al archivo objeto de salida.

Vaya al procedimiento [Para vincular las pruebas a los archivos de biblioteca u objeto](#objectRef).

**Las pruebas unitarias llaman a funciones que no son miembro y que no se exportan desde la DLL, y la DLL se puede compilar como una biblioteca estática:** cambie el proyecto de DLL para que se compile en un archivo *.lib*. Agregue un proyecto de prueba independiente que haga referencia al proyecto en pruebas.

Este método tiene la ventaja de permitir que las pruebas usen miembros no exportados, pero sigue manteniendo las pruebas en un proyecto independiente.

Vaya al procedimiento [Para cambiar la DLL a una biblioteca estática](#staticLink).

**Las pruebas unitarias deben llamar a funciones que no son miembro y que no se han exportado, y el código debe compilarse como una biblioteca de vínculos dinámicos (DLL):** agregue pruebas unitarias en el mismo proyecto que el código de producto.

Vaya al procedimiento [Para agregar pruebas unitarias en el mismo proyecto](#sameProject).

## <a name="create-the-tests"></a>Crear las pruebas

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Para cambiar la DLL a una biblioteca estática

- Si las pruebas deben usar miembros que el proyecto DLL no ha exportado y el proyecto se compila como una biblioteca dinámica, considere convertirla en una biblioteca estática.

  1. En el **Explorador de soluciones**, en el menú contextual del proyecto en pruebas, seleccione **Propiedades**. Se abrirá la ventana de **propiedades** del proyecto.

  2. Seleccione **Propiedades de configuración** > **General**.

  3. Establezca **Tipo de configuración** en **Biblioteca estática (.lib)**.

  Continúe con el procedimiento [Para vincular las pruebas a los archivos de biblioteca u objeto](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Para hacer referencia a funciones de DLL exportadas del proyecto de prueba

- Si un proyecto DLL exporta funciones que quiere probar, puede agregar una referencia al proyecto de código desde el proyecto de prueba.

  1. Cree un proyecto de prueba unitaria nativo.

      ::: moniker range="vs-2019"

      1. En el menú **Archivo**, elija **Nuevo** > **Proyecto**. En el cuadro de diálogo **Agregar un proyecto nuevo** establezca el valor de **Lenguaje** en C++ y escriba "prueba" en el cuadro de búsqueda. Después, elija el **proyecto de prueba unitaria de tipo nativo**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto** > **Visual C++** > **Prueba** > **Proyecto de prueba unitaria C++**.

      ::: moniker-end

  1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de prueba y, a continuación, elija **Agregar** > **Referencia**.

  1. Seleccione **Proyectos** y, después, el proyecto que se va a probar.

       Elija el botón **Agregar**.

  1. En las propiedades del proyecto de prueba, agregue la ubicación del proyecto en pruebas a los directorios de archivos de inclusión.

       Seleccione **Propiedades de configuración** > **Directorios de VC++**  > **Directorios de archivos de inclusión**.

       Elija **Editar** y agregue el directorio del encabezado del proyecto en pruebas.

  Vaya a [Escribir las pruebas unitarias](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Para vincular las pruebas a los archivos de biblioteca u objeto

- Si la DLL no exporta las funciones que quiere probar, puede agregar el archivo de salida *.obj* o *.lib* a las dependencias del proyecto de prueba.

  1. Cree un proyecto de prueba unitaria nativo.

      ::: moniker range="vs-2019"

      1. En el menú **Archivo**, elija **Nuevo** > **Proyecto**. En el cuadro de diálogo **Agregar un proyecto nuevo** establezca el valor de **Lenguaje** en C++ y escriba "prueba" en el cuadro de búsqueda. Después, elija el **proyecto de prueba unitaria de tipo nativo**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto** > **Visual C++** > **Prueba** > **Proyecto de prueba unitaria C++**.

      ::: moniker-end

  2. En el **Explorador de soluciones**, en el menú contextual del proyecto de prueba, seleccione **Propiedades**.

  3. Elija **Propiedades de configuración** > **Vinculador** > **Entrada** > **Dependencias adicionales**.

       Seleccione **Editar** y agregue los nombres de los archivos **.obj** o **.lib**. No utilice nombres de ruta de acceso completa.

  4. Elija **Propiedades de configuración** > **Enlazador** > **General** > **Directorios de bibliotecas adicionales**.

       Seleccione **Editar** y agregue la ruta del directorio de los archivos **.obj** o **.lib**. La ruta de acceso está normalmente dentro de la carpeta de compilación del proyecto en pruebas.

  5. Seleccione **Propiedades de configuración** > **Directorios de VC++**  > **Directorios de archivos de inclusión**.

       Elija **Editar** y agregue el directorio del encabezado del proyecto en pruebas.

  Vaya a [Escribir las pruebas unitarias](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Para agregar pruebas unitarias en el mismo proyecto

1. Modifique las propiedades del proyecto de código del producto para incluir los encabezados y los archivos de biblioteca que se requieren para pruebas unitarias.

   1. En el **Explorador de soluciones**, en el menú contextual del proyecto en pruebas, seleccione **Propiedades**. Se abrirá la ventana de **propiedades** del proyecto.

   2. Elija **Propiedades de configuración** > **Directorios de VC++** .

   3. Edite los directorios de inclusión y de biblioteca:

       |Directorio|Propiedad.|
       |-|-|
       |**Directorios de archivos de inclusión** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Directorios de archivos de bibliotecas** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Agregue el archivo de prueba unitaria de C++:

   - En el **Explorador de soluciones**, en el menú contextual del proyecto, elija **Agregar** > **Nuevo elemento** > **Pruebas unitarias de C++**.

   Vaya a [Escribir las pruebas unitarias](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Escribir las pruebas unitarias

1. En cada archivo de código de prueba unitaria, agregue un fragmento `#include` para los encabezados de proyecto en pruebas.

2. Agregue las clases y los métodos de prueba a los archivos de código de prueba unitaria. Por ejemplo:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Ejecutar las pruebas

1. En el menú **Prueba**, elija **Windows** > **Explorador de pruebas**.

1. Si ninguna de las pruebas está visible en la ventana, compile el proyecto de prueba haciendo clic con el botón derecho en el nodo correspondiente en el **Explorador de soluciones** y eligiendo **Compilar** o **Recompilar**.

1. En el **Explorador de pruebas**, elija **Ejecutar todas** o seleccione las pruebas concretas que quiera ejecutar. Haga clic con el botón derecho en una prueba para ver otras opciones, como la ejecución en modo de depuración con puntos de interrupción habilitados.

## <a name="see-also"></a>Consulte también

- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)
- [Referencia de API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Depuración del código nativo](../debugger/debugging-native-code.md)
- [Tutorial: Creación y uso de una biblioteca de vínculos dinámicos (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importación y exportación](/cpp/build/importing-and-exporting)
- [Inicio rápido: Desarrollo controlado por pruebas con el Explorador de pruebas](../test/quick-start-test-driven-development-with-test-explorer.md)

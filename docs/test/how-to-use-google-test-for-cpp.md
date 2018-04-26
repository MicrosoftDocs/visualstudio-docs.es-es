---
title: Cómo usar Google Test para C++ en Visual Studio
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: c5e86884f017aa2fc490eb926485c567742b8647
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Cómo usar Google Test para C++ en Visual Studio
En la **versión 15.5 de Visual Studio 2017** y en versiones posteriores, Google Test se integra en el IDE de Visual Studio como un componente predeterminado de la carga de trabajo de **desarrollo para el escritorio con C++**. Para comprobar que está instalado en su equipo, abra al Instalador de Visual Studio y busque Google Test en la lista de componentes de carga de trabajo:

![Instalación de Google Test](media/cpp-google-component.png "Instalar Google Test para C++")

## <a name="add-a-google-test-project-to-the-solution"></a>Agregar un proyecto de Google Test a la solución
1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar | Nuevo proyecto**.
2. En el panel izquierdo, elija **Visual C++ | Prueba** y, después, elija el proyecto de **Google Test** en el panel central.
3. Asigne un nombre al proyecto de Google Test y haga clic en **Aceptar**.

![Nuevo proyecto de Google Test](media/cpp-gtest-new-project.png "Agregar un nuevo proyecto de Google Test")

## <a name="configure-the-test-project"></a>Configurar el proyecto de prueba
En el cuadro de diálogo **Configuración del proyecto de prueba** que se abre, puede elegir el proyecto que quiere probar. Cuando se elige un proyecto, Visual Studio agrega una referencia al proyecto seleccionado. Si no se elige ninguno, deberá agregar manualmente las referencias a los proyectos que quiere probar. Al elegir entre vínculos estáticos y dinámicos para los archivos binarios de Google Test, las consideraciones son las mismas que para cualquier programa de C++. Para más información, vea [DLLs in Visual C++](/cpp/build/dlls-in-visual-cpp) (DLL en Visual C++).

 ![Configurar proyecto de Google Test](media/cpp-gtest-config.png "Configurar proyecto de Google Test")

## <a name="set-additional-options"></a>Definir más opciones
En el menú principal, elija **Herramientas | Opciones | Test Adapter para Google Test** para definir más opciones. Vea la documentación de Google Test para más información sobre estas opciones.

 ![Configuración del proyecto de Google Test](media/cpp-gtest-settings.png "Configuración del proyecto de Google Test")

## <a name="add-include-directives"></a>Agregar directivas include
En el archivo .cpp de prueba, agregue las directivas `#include` que sean necesarias para que los tipos y funciones del programa estén visibles en el código de prueba. El programa suele estar un nivel por encima en la jerarquía de carpetas. Si escribe `#include "../"`, se abrirá una ventana de IntelliSense donde podrá seleccionar la ruta de acceso completa al archivo de encabezado.

![Agregar directivas #include](media/cpp-gtest-includes.png "Agregar directivas #include al archivo .cpp de prueba")

## <a name="write-and-run-tests"></a>Escribir y ejecutar pruebas
Ya está listo para escribir y ejecutar pruebas de Google Test. Vea [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md) para más información sobre las macros de prueba. Vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) para más información sobre cómo detectar, ejecutar y agrupar las pruebas usando el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también
[Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)











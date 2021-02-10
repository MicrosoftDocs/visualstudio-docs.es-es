---
title: Cómo usar Google Test para C++
description: Use Google Test para crear pruebas unitarias de C++ en Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 6cf29d16432b677c6e83ba4cbaedb39f0a8d1ed2
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572998"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Cómo usar Google Test para C++ en Visual Studio

En Visual Studio 2017 y versiones posteriores, Google Test se integra en el IDE de Visual Studio como un componente predeterminado de la carga de trabajo **Desarrollo para el escritorio con C++** . Para comprobar que está instalado en su equipo, abra al Instalador de Visual Studio y busque Google Test en la lista de componentes de carga de trabajo:

![Instalar Google Test](media/cpp-google-component.png)

::: moniker range="vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Agregación de un proyecto de Google Test en Visual Studio 2019

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar** > **Nuevo proyecto**.
2. Establezca el valor de **Lenguaje** en **C++** y escriba **prueba** en el cuadro de búsqueda. En la lista de resultados, elija **Proyecto de Google Test**.
3. Asigne un nombre al proyecto de Google Test y haga clic en **Aceptar**.

![Nuevo proyecto de Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Agregación de un proyecto de Google Test en Visual Studio 2017

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución y elija **Agregar** > **Nuevo proyecto**.
2. En el panel izquierdo, elija **Visual C++** > **Prueba** y, luego, seleccione **Proyecto de Google Test** en el panel central.
3. Asigne un nombre al proyecto de Google Test y haga clic en **Aceptar**.

![Nuevo proyecto de Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Configurar el proyecto de prueba

En el cuadro de diálogo **Configuración del proyecto de prueba** que se abre, puede elegir el proyecto que quiere probar. Cuando se elige un proyecto, Visual Studio agrega una referencia al proyecto seleccionado. Si no se elige ninguno, deberá agregar manualmente las referencias a los proyectos que quiere probar. Al elegir entre vínculos estáticos y dinámicos para los archivos binarios de Google Test, las consideraciones son las mismas que para cualquier programa de C++. Para más información, vea [DLLs in Visual C++](/cpp/build/dlls-in-visual-cpp) (DLL en Visual C++).

![Configurar el proyecto Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Definir más opciones

En el menú principal, elija **Herramientas** > **Opciones** > **Test Adapter para Google Test** para definir más opciones. Vea la documentación de Google Test para más información sobre estas opciones.

![Configuración del proyecto de Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Agregar directivas include

En el archivo *.cpp* de prueba, agregue las directivas `#include` que sean necesarias para que los tipos y funciones del programa estén visibles en el código de prueba. El programa suele estar un nivel por encima en la jerarquía de carpetas. Si escribe `#include "../"`, se abrirá una ventana de IntelliSense donde podrá seleccionar la ruta de acceso completa al archivo de encabezado.

![Agregar directivas #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Escribir y ejecutar pruebas

Ya está listo para escribir y ejecutar pruebas de Google Test. Vea [Google Test Primer](https://github.com/google/googletest/blob/master/docs/primer.md) para obtener más información sobre las macros de prueba. Vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) para más información sobre cómo detectar, ejecutar y agrupar las pruebas usando el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también

[Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

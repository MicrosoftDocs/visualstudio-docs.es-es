---
title: "Cómo usar CTest para C++ en Visual Studio | Microsoft Docs"
ms.date: 11/07/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 602240df366d9ee978f632a8693bae3de21fcedf
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Cómo usar CTest para C++ en Visual Studio

CMake (que incluye CTest) se integra en el IDE de Visual Studio de manera predeterminada como un componente de la carga de trabajo **Desarrollo para el escritorio con C++**. Si necesita instalarlo en su equipo, abra el programa Instalador de Visual Studio, haga clic en el botón **Modificar** y compruebe las [herramientas de CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) en la lista de componentes de la carga de trabajo.

## <a name="to-write-tests"></a>Para escribir pruebas

La compatibilidad con CMake en Visual Studio no tiene que ver con el sistema de proyectos de Visual Studio. Por lo tanto, puede escribir y configurar pruebas de CTest del mismo modo en que lo hace en cualquier entorno de CMake. Para información sobre cómo usar CMake en Visual Studio, consulte el artículo sobre las [herramientas de CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Para ejecutar pruebas (versión 15.6 de Visual Studio 2017)

En la versión 15.6 de Visual Studio 2017, CTest está completamente integrado con el **Explorador de pruebas** y también es compatible con los marcos de pruebas sanitarias de Google y Boost. Esos marcos se incluyen de manera predeterminada como componentes en la carga de trabajo **Desarrollo para el escritorio con C++**. Sin embargo, si actualiza un proyecto de una versión anterior de Visual Studio, puede que tenga que instalar esos marcos con el programa Instalador de Visual Studio.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en VS2017 15.6](media/ctest-test-explorer.png "CTest y Google Test en el Explorador de pruebas")

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Para ejecutar pruebas (versión 15.5 de Visual Studio 2017)

En la **versión 15.5 de Visual Studio 2017**, CTest no está integrado con el **Explorador de pruebas**. Puede ejecutar las pruebas desde el menú principal de CMake o desde el menú contextual, en un archivo **CMakeLists.txt** en el **Explorador de soluciones**. Los resultados de las pruebas van a la **Ventana de salida** de Visual Studio.

![Ejecución de pruebas de CTest en VS2017 15.5](media/cpp-cmake-run-tests.png "Ejecución de pruebas de CTest en 15.5")

## <a name="see-also"></a>Vea también

[Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)
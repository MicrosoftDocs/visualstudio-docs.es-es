---
title: Cómo usar CTest para C++
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: d02c4546b98e2a7551f4454088acfc6a54637e4f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925464"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Cómo usar CTest para C++ en Visual Studio

CMake (que incluye CTest) se integra en el IDE de Visual Studio de manera predeterminada como un componente de la carga de trabajo **Desarrollo para el escritorio con C++**. Si necesita instalarlo en su equipo, abra el programa Instalador de Visual Studio, haga clic en el botón **Modificar** y active [Herramientas de CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) en la lista de componentes de carga de trabajo.

## <a name="to-write-tests"></a>Para escribir pruebas

La compatibilidad con CMake en Visual Studio no tiene que ver con el sistema de proyectos de Visual Studio. Por lo tanto, puede escribir y configurar pruebas de CTest del mismo modo en que lo hace en cualquier entorno de CMake. Para obtener más información sobre cómo usar CMake en Visual Studio, vea el artículo sobre las [herramientas de CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Para ejecutar pruebas (versión 15.6 de Visual Studio 2017)

En la versión 15.6 de Visual Studio 2017, CTest está completamente integrado con el **Explorador de pruebas** y también es compatible con los marcos de pruebas sanitarias de Google y Boost. Esos marcos se incluyen de manera predeterminada como componentes en la carga de trabajo **Desarrollo para el escritorio con C++**. Sin embargo, si actualiza un proyecto de una versión anterior de Visual Studio, puede que tenga que instalar esos marcos con el programa Instalador de Visual Studio.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en VS2017 15.6](media/ctest-test-explorer.png)

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Para ejecutar pruebas (versión 15.5 de Visual Studio 2017)

En la **versión 15.5 de Visual Studio 2017**, CTest no está integrado con el **Explorador de pruebas**. Puede ejecutar las pruebas desde el menú principal de CMake o desde el menú contextual, en un archivo *CMakeLists.txt* en el **Explorador de soluciones**. Los resultados de las pruebas van a la **Ventana de salida** de Visual Studio.

![Ejecutar pruebas de CTest en VS2017 15.5](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>Vea también

[Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)
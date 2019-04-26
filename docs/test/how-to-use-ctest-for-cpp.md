---
title: Cómo usar CTest para C++
ms.date: 11/07/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 6be079a5adfe52a7ac750f6713672dad50c7d2a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945391"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Cómo usar CTest para C++ en Visual Studio

CMake (que incluye CTest) se integra en el IDE de Visual Studio de manera predeterminada como un componente de la carga de trabajo **Desarrollo para el escritorio con C++**. Si necesita instalarlo en su equipo, abra el programa Instalador de Visual Studio, haga clic en el botón **Modificar** y active [Herramientas de CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) en la lista de componentes de carga de trabajo.

## <a name="to-write-tests"></a>Para escribir pruebas

La compatibilidad con CMake en Visual Studio no tiene que ver con el sistema de proyectos de Visual Studio. Por lo tanto, puede escribir y configurar pruebas de CTest del mismo modo en que lo hace en cualquier entorno de CMake. Para obtener más información sobre cómo usar CMake en Visual Studio, vea el artículo sobre las [herramientas de CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests"></a>Para ejecutar pruebas

::: moniker range="vs-2017"

### <a name="visual-studio-2017-version-156-and-later"></a>Visual Studio 2017 versión 15.6 y posteriores

En la versión 15.6 y posteriores de Visual Studio 2017, CTest está completamente integrado con el **Explorador de pruebas** y también es compatible con los marcos de pruebas unitarias de Google y Boost. Esos marcos se incluyen de manera predeterminada como componentes en la carga de trabajo **Desarrollo para el escritorio con C++**. Sin embargo, si actualiza un proyecto de una versión anterior de Visual Studio, puede que tenga que instalar esos marcos con el programa Instalador de Visual Studio.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en Visual Studio 2017](media/ctest-test-explorer.png)

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

En la versión 15.5 de Visual Studio 2017, CTest no está integrado con el **Explorador de pruebas**. Puede ejecutar las pruebas desde el menú principal de CMake, o bien desde el menú contextual en un archivo *CMakeLists.txt* en el **Explorador de soluciones**. Los resultados de las pruebas van a la **Ventana de salida** de Visual Studio.

![Ejecutar pruebas CTest en Visual Studio 2017 versión 15.5](media/cpp-cmake-run-tests.png)

::: moniker-end

::: moniker range=">=vs-2019"

CTest está completamente integrado con el **Explorador de pruebas** y también es compatible con los marcos de pruebas unitarias de Google y Boost. Esos marcos se incluyen de manera predeterminada como componentes en la carga de trabajo **Desarrollo para el escritorio con C++**. Sin embargo, si actualiza un proyecto de una versión anterior de Visual Studio, puede que tenga que instalar esos marcos con el programa Instalador de Visual Studio.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en Visual Studio](media/ctest-test-explorer.png)

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

::: moniker-end

## <a name="see-also"></a>Vea también

- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)
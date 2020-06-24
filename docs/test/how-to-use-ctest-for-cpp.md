---
title: Cómo usar CTest para C++
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: c429c9e676ead54bb9f168e3220bf2d4791fac63
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287238"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Cómo usar CTest para C++ en Visual Studio 2017 y versiones posteriores

CMake (que incluye CTest) se integra en el IDE de Visual Studio de manera predeterminada como un componente de la carga de trabajo **Desarrollo para el escritorio con C++** . En caso de que deba instalarlo en su máquina, abra el programa de instalación de Visual Studio, haga clic en el botón **Desarrollo para el escritorio con C++** y después seleccione **Modificar**. Seleccione **Herramientas de CMake en C++ para Windows** en la lista de componentes de carga de trabajo.

## <a name="to-write-tests"></a>Para escribir pruebas

La compatibilidad con CMake en Visual Studio no tiene que ver con el sistema de proyectos de Visual Studio. Por lo tanto, puede escribir y configurar pruebas de CTest del mismo modo en que lo hace en cualquier entorno de CMake. Use el comando `enable_testing()` para habilitar las pruebas y el comando `add_test()` o `gtest_discover_tests()` para agregar una prueba nueva. Para más información sobre CTest, consulte la [documentación de CMake](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Para obtener más información sobre cómo usar CMake en Visual Studio, consulte el artículo sobre los [proyectos de CMake en Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Para ejecutar pruebas

CTest está completamente integrado con el **Explorador de pruebas** y también es compatible con los marcos de pruebas unitarias de Google y Boost. Esos marcos se incluyen de manera predeterminada como componentes en la carga de trabajo **Desarrollo para el escritorio con C++** . Sin embargo, si actualiza un proyecto de una versión anterior de Visual Studio, puede que tenga que instalar esos marcos con el programa Instalador de Visual Studio.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en Visual Studio](media/ctest-test-explorer.png)

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

## <a name="see-also"></a>Vea también

- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

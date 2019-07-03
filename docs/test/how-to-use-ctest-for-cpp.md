---
title: Cómo usar CTest para C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 0b6c4eb391014342a18ec3fe56a03a651463105c
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160090"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Cómo usar CTest para C++ en Visual Studio 2017 y versiones posteriores

CMake (que incluye CTest) se integra en el IDE de Visual Studio de manera predeterminada como un componente de la carga de trabajo **Desarrollo para el escritorio con C++** . En caso de que deba instalarlo en su máquina, abra el programa de instalación de Visual Studio, haga clic en el botón **Desarrollo para el escritorio con C++** y después seleccione **Modificar**. Seleccione **Herramientas de CMake en C++ para Windows** en la lista de componentes de carga de trabajo.

## <a name="to-write-tests"></a>Para escribir pruebas

La compatibilidad con CMake en Visual Studio no tiene que ver con el sistema de proyectos de Visual Studio. Por lo tanto, puede escribir y configurar pruebas de CTest del mismo modo en que lo hace en cualquier entorno de CMake. Para obtener más información sobre cómo usar CMake en Visual Studio, consulte el artículo sobre los [proyectos de CMake en Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Para ejecutar pruebas

CTest está completamente integrado con el **Explorador de pruebas** y también es compatible con los marcos de pruebas unitarias de Google y Boost. Esos marcos se incluyen de manera predeterminada como componentes en la carga de trabajo **Desarrollo para el escritorio con C++** . Sin embargo, si actualiza un proyecto de una versión anterior de Visual Studio, puede que tenga que instalar esos marcos con el programa Instalador de Visual Studio.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en Visual Studio](media/ctest-test-explorer.png)

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

En la ilustración siguiente se muestran los resultados de una ejecución de CTest con el marco de Google Test:

![CTest con el marco de Google Test en Visual Studio 2017](media/ctest-test-explorer.png)

Si usa CTest pero no los adaptadores de Google ni Boost, verá los resultados en el nivel de CTest en lugar del nivel del método de prueba individual. Puede depurar paso a paso los archivos ejecutables solo de CTest, pero no se admiten los seguimientos de la pila en las pruebas individuales.

## <a name="see-also"></a>Vea también

- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

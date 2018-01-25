---
title: "Cómo usar CTest para C++ en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 529e070a3db1e6587989f8d0c55dc04e6db0388c
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Cómo usar CTest para C++ en Visual Studio
CMake (que incluye CTest) se integra en el IDE de Visual Studio como un componente de la carga de trabajo de **desarrollo para el escritorio con C++**. Para instalarlo en su equipo, abra al Instalador de Visual Studio y busque [CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) en la lista de componentes de carga de trabajo.

La compatibilidad con CMake en Visual Studio no tiene que ver con el sistema de proyectos de Visual Studio. Por lo tanto, puede escribir y configurar pruebas de CTest del mismo modo en que lo hace en cualquier entorno de CMake. Vea [CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) (CMake Tools para Visual C++) para más información sobre cómo usar CMake en Visual Studio.

En la **versión 15.5 de Visual Studio 2017**, CTest no está integrado actualmente con el **Explorador de pruebas**. Puede ejecutar las pruebas desde el menú principal de CMake o desde el menú contextual, en un archivo **CMakeLists.txt** en el **Explorador de soluciones**. Los resultados de las pruebas van a la **Ventana de salida** de Visual Studio.

![Ejecutar pruebas de CTest](media/cpp-cmake-run-tests.png "Ejecutar pruebas de CTest")

## <a name="see-also"></a>Vea también
[Escribir pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)
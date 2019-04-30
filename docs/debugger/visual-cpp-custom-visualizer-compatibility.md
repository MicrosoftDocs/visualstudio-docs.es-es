---
title: Visual C /C++ compatibilidad visualizador personalizado
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901171"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C /C++ compatibilidad visualizador personalizado

A partir de Visual Studio 2019, Visual C++ incluye un depurador mejorado que usa un proceso externo de 64 bits para hospedar sus componentes gran cantidad de memoria. Como parte de esta actualización, determinadas extensiones de Visual C /C++ evaluador debe actualizarse para que sean compatibles con el depurador de nuevo.

Si está utilizando actualmente una C heredada /C++ EE addin o C /C++ visualizador personalizado, puede desactivar el uso de este proceso externo, vaya a **herramientas** > **opciones**  >  **Depuración**y, a continuación, anule la selección de **símbolos de depuración de la carga en el proceso externo (solo nativo)**. Si desactiva esta opción, se producirá un aumento significativo en el uso de memoria dentro del proceso IDE (devenv.exe). Por lo tanto, si piensa depurar proyectos de gran tamaño, se recomienda que trabaje con el propietario de la extensión para que sea compatible con esta opción de depuración.

Si es el propietario de un C heredado /C++ EE addin o C /C++ visualizador personalizado, puede encontrar más información sobre optar al cargar la extensión en un proceso de trabajo en el [wiki de ejemplos de extensibilidad Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). También puede encontrar un [C /C++ ejemplo visualizador personalizado](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
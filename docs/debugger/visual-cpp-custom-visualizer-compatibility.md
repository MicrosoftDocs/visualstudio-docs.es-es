---
title: Compatibilidad de visualizador personalizado Visual C/c ++
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
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: a51f2d87b432bf6f4a3925b55622273b56cf5c32
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920969"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilidad de visualizador personalizado Visual C/c ++

A partir de 2019 de Visual Studio, Visual C++ incluye a un depurador mejorado que usa un proceso externo de 64 bits para hospedar sus componentes gran cantidad de memoria. Como parte de esta actualización, determinadas extensiones en el evaluador de expresiones de Visual C/C ++ deben actualizarse para que sean compatibles con el depurador de nuevo.

Si está utilizando actualmente un heredado addin EE de C o C++ o un visualizador personalizado de C o C++, puede desactivar el uso de este proceso externo, vaya a **herramientas** > **opciones**  >   **Depuración**y, a continuación, anule la selección de **símbolos de depuración de la carga en el proceso externo (solo nativo)**. Si desactiva esta opción, se producirá un aumento significativo en el uso de memoria dentro del proceso IDE (devenv.exe). Por lo tanto, si piensa depurar proyectos de gran tamaño, se recomienda que trabaje con el propietario de la extensión para que sea compatible con esta opción de depuración.

Si es el propietario de un addin de C o C++ EE heredado o visualizador personalizado de C o C++, puede encontrar más información sobre optar al cargar la extensión en un proceso de trabajo en el [wiki de ejemplos de extensibilidad Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). También puede encontrar un [ejemplo de C o C++ visualizador personalizado](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
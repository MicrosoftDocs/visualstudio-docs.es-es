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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335186"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilidad de visualizador personalizado Visual C/c ++

A partir de 2019 de Visual Studio, Visual C++ incluye a un depurador mejorado que usa un proceso externo de 64 bits para hospedar sus componentes gran cantidad de memoria. Como parte de esta actualización, determinadas extensiones en el evaluador de expresiones de Visual C/C ++ deben actualizarse para que sean compatibles con el depurador de nuevo.

Si está utilizando actualmente un heredado addin EE de C o C++ o un visualizador personalizado de C o C++, puede desactivar el uso de este proceso externo, vaya a **herramientas** > **opciones**  >   **Depuración**y, a continuación, anule la selección de **símbolos de depuración de la carga en el proceso externo (solo nativo)**. Si desactiva esta opción, se producirá un aumento significativo en el uso de memoria dentro del proceso IDE (devenv.exe). Por lo tanto, si piensa depurar proyectos de gran tamaño, se recomienda que trabaje con el propietario de la extensión para que sea compatible con esta opción de depuración.

Si es el propietario de un addin de C o C++ EE heredado o visualizador personalizado de C o C++, puede encontrar más información sobre optar al cargar la extensión en un proceso de trabajo en el [wiki de ejemplos de extensibilidad Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). También puede encontrar un [ejemplo de C o C++ visualizador personalizado](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
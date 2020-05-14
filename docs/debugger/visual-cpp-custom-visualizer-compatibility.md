---
title: Compatibilidad del visualizador personalizado de Visual C/C++
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430621"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilidad del visualizador personalizado de Visual C/C++

A partir de Visual Studio 2019, C++ incluye un depurador mejorado que utiliza un proceso externo de 64 bits para hospedar sus componentes de uso intensivo de memoria. Como parte de esta actualización, ciertas extensiones del evaluador de expresiones de C/C++ deben actualizarse para que sean compatibles con el nuevo depurador.

Si actualmente está consumiendo un complemento de C/C++ EE heredado o un visualizador personalizado de C/C++, puede desactivar el uso de este proceso externo; para ello, vaya a **Herramientas** > **Opciones** > **Depuración** y, a continuación, anule la selección de **Cargar símbolos de depuración en proceso externo (solo nativo)** . Si anula la selección de esta opción, se producirá un aumento significativo del uso de memoria dentro del proceso del IDE (devenv.exe). Por lo tanto, si espera depurar proyectos grandes, se recomienda que trabaje con el propietario de la extensión para que sea compatible con esta opción de depuración.

Si es el propietario de un complemento de C/C++ EE heredado o un visualizador personalizado de C++, puede encontrar más información sobre cómo optar por cargar la extensión en un proceso de trabajo en la [wiki de ejemplos de extensibilidad de Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). También puede encontrar un [ejemplo del visualizador personalizado de C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
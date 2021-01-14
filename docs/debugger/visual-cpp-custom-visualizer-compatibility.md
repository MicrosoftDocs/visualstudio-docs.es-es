---
title: Compatibilidad del visualizador personalizado de Visual C/C++
description: Es posible que una nueva característica de Visual Studio 2019 no sea compatible con los complementos del evaluador de expresiones de C/C++ heredados ni con los visualizadores personalizados. Consulta este artículo para obtener más información.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dea92f6aad54b8c75c43a1078142595e17fa2ef6
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149799"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilidad del visualizador personalizado de Visual C/C++

A partir de Visual Studio 2019, C++ incluye un depurador mejorado que utiliza un proceso externo de 64 bits para hospedar sus componentes de uso intensivo de memoria. Como parte de esta actualización, ciertas extensiones del evaluador de expresiones de C/C++ deben actualizarse para que sean compatibles con el nuevo depurador.

Si está consumiendo un complemento de C/C++ EE heredado o un visualizador personalizado de C/C++, puede desactivar el uso de este proceso externo. Para ello, vaya a **Herramientas** > **Opciones** > **Depuración** y, luego, anule la selección de **Cargar símbolos de depuración en proceso externo (solo nativo)** . Si anula la selección de esta opción, se producirá un aumento significativo del uso de memoria dentro del proceso del IDE (devenv.exe). Por lo tanto, si espera depurar proyectos grandes, se recomienda que trabaje con el propietario de la extensión para que sea compatible con esta opción de depuración.

Si es el propietario de un complemento de C/C++ EE heredado o un visualizador personalizado de C++, puede encontrar más información sobre cómo optar por cargar la extensión en un proceso de trabajo en la [wiki de ejemplos de extensibilidad de Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). También puede encontrar un [ejemplo del visualizador personalizado de C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).
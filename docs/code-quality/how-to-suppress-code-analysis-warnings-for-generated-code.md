---
title: Suprimir las infracciones de análisis de código para el código generado
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ee4e3df94e46b4d3cc996a23fc1e40401195e21
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551134"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedimiento Suprimir advertencias de análisis de código para código generado

El código generado incluye el código que el compilador de código administrado o las herramientas de terceros agregan al proyecto. Es posible que desee ver las infracciones de las reglas que el análisis de código detecta en el código generado. Sin embargo, puesto que no puede ver y mantener el código que contiene las infracciones, es posible que no desee verlos.

La casilla **suprimir resultados de código generado** en la página de propiedades análisis de código de un proyecto permite seleccionar si se van a mostrar advertencias de análisis de código del código generado por una herramienta de terceros.

> [!NOTE]
> Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir las advertencias del código generado en un proyecto

1. Haga clic con el botón secundario en el proyecto en **Explorador de soluciones** y, a continuación, haga clic en **propiedades**.

2. Elija la pestaña **análisis de código** .

3. Active la casilla **suprimir resultados de código generado** .

> [!NOTE]
> Solo puede suprimir las advertencias del análisis heredado. Actualmente, no se pueden suprimir las advertencias de análisis de código de los [analizadores](roslyn-analyzers-overview.md).
---
title: Suprimir las infracciones de análisis de código para código generado
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613569"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedimiento Suprimir advertencias de análisis de código para código generado

Código generado incluye código que se agrega al proyecto mediante los compiladores de código administrado o herramientas de terceros. Es posible que desea ver las infracciones de regla que detecta el análisis de código en el código generado. Sin embargo, dado que no se puede ver y mantener el código que contiene las infracciones, es posible que no desea verlos.

El **Suprimir resultados del código generado** casilla de verificación en la página de propiedades de análisis de código de un proyecto le permite seleccionar si se muestran las advertencias de análisis de código generado por una herramienta de terceros de código.

> [!NOTE]
> Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir advertencias de código generado en un proyecto

1. Haga clic en el proyecto en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades**.

2. Elija la **análisis de código** ficha.

3. Seleccione el **Suprimir resultados del código generado** casilla de verificación.

> [!NOTE]
> Sólo puede suprimir las advertencias de análisis de código estático. Actualmente, no se puede suprimir advertencias de análisis de código de [analizadores](roslyn-analyzers-overview.md).
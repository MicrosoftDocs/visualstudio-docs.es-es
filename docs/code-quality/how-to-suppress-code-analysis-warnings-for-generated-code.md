---
title: Suprimir las infracciones de análisis de código para el código generado
ms.date: 05/13/2019
description: Obtenga información sobre cómo suprimir advertencias de análisis de código para el código generado. Vea cómo evitar que Visual Studio muestre advertencias de análisis heredado sobre el código generado.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a149511b447f1f21d180eaf526ebc3d991c95997
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859949"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Cómo: suprimir advertencias de análisis de código para el código generado

El código generado incluye el código que el compilador de código administrado o las herramientas de terceros agregan al proyecto. Es posible que desee ver las infracciones de las reglas que el análisis de código detecta en el código generado. Sin embargo, puesto que no puede ver y mantener el código que contiene las infracciones, es posible que no desee verlos.

La casilla **suprimir resultados de código generado** en la página de propiedades análisis de código de un proyecto permite seleccionar si se van a mostrar advertencias de análisis de código del código generado por una herramienta de terceros.

> [!NOTE]
> Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir las advertencias del código generado en un proyecto

1. Haga clic con el botón secundario en el proyecto en **Explorador de soluciones** y, a continuación, haga clic en **propiedades**.

2. Elija la pestaña **análisis de código** .

3. Active la casilla **suprimir resultados de código generado** .

> [!IMPORTANT]
> Solo puede suprimir las advertencias del análisis heredado. La página de propiedades con la opción está en desuso y se quitará en una versión futura del producto. Actualmente, no se pueden suprimir las advertencias de análisis de código de los [analizadores](roslyn-analyzers-overview.md).

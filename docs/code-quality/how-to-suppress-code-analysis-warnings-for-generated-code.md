---
title: Procedimiento Suprimir advertencias de análisis de código para código generado
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a69d2006f5fbacd213f86f2091c019fcc468d10
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403128"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procedimiento Suprimir advertencias de análisis de código para código generado
Compiladores de código administrado a menudo generan código que se agrega a un proyecto para facilitar el desarrollo rápido de código. Además, los desarrolladores suelen utilizar herramientas de terceros para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas también generan código que se agrega al proyecto.

 Es posible que desea ver las infracciones de regla que detecta el análisis de código en el código generado. Sin embargo, es posible que no desea verlos si no se puede ver y mantener el código que contiene la infracción.

 El **Suprimir resultados del código generado** casilla de verificación en la página de propiedades de análisis de código de un proyecto le permite seleccionar si desea ver las advertencias de análisis de código desde el código generado por una herramienta de terceros.

> [!NOTE]
> Esta opción no suprime los errores de análisis de código y las advertencias de código generado cuando los errores y advertencias aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir advertencias de código generado en un proyecto

1. Haga clic en el proyecto en el Explorador de soluciones y, a continuación, haga clic en **propiedades**.

2. Haga clic en **análisis de código**.

3. Seleccione el **Suprimir resultados del código generado** casilla de verificación.
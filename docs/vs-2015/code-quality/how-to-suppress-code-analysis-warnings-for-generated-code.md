---
title: 'Cómo: suprimir advertencias de análisis de código para código generado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646274"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Cómo: Suprimir advertencias de análisis de código en código generado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los compiladores de código administrado suelen generar código que se agrega a un proyecto para facilitar el desarrollo rápido de código. Además, los desarrolladores suelen usar herramientas de terceros para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas también generan código que se agrega al proyecto.

 Es posible que desee ver las infracciones de las reglas que el análisis de código detecta en el código generado. Sin embargo, es posible que no desee verlas si no puede ver y mantener el código que contiene la infracción.

 La casilla **suprimir resultados de código generado** en la página de propiedades análisis de código de un proyecto permite seleccionar si desea ver las advertencias de análisis de código del código generado por una herramienta de terceros.

> [!NOTE]
> Esta opción no suprime los errores y las advertencias de análisis de código del código generado cuando los errores y las advertencias aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir las advertencias del código generado en un proyecto

1. Haga clic con el botón secundario en el proyecto en Explorador de soluciones y, a continuación, haga clic en **propiedades**.

2. Haga clic en **análisis de código**.

3. Active la casilla **suprimir resultados de código generado** .

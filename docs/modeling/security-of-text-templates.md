---
title: Seguridad de las plantillas de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bb5ad4348d681a2b7bc59c588bb74e0a27813e73
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820817"
---
# <a name="security-of-text-templates"></a>Seguridad de las plantillas de texto
Las plantillas de texto tienen los siguientes problemas de seguridad:

-   Las plantillas de texto son vulnerables a las inserciones de código arbitrario.

-   Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, se podría ejecutar un procesador de directivas malintencionado.

## <a name="arbitrary-code"></a>Código arbitrario
 Al escribir una plantilla, puede colocar cualquier código dentro de la \<## > etiquetas. Esto permite que el código arbitrario para ejecutarse desde una plantilla de texto.

 Asegúrese de que obtener las plantillas de orígenes de confianza. Asegúrese de que advertir a los usuarios finales de su aplicación no ejecutar plantillas que no procedan de fuentes de confianza.

## <a name="malicious-directive-processor"></a>Procesador de directivas malintencionado
 El motor de plantillas de texto interactúa con un host de transformación y uno o más procesadores de directivas para transformar el texto de la plantilla en un archivo de salida. Para obtener más información, consulte [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).

 Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, se corre el riesgo de la ejecución de un procesador de directivas malintencionado. El procesador de directivas malintencionado podría proporcionar código que se ejecuta en `FullTrust` modo cuando se ejecuta la plantilla. Si crea un host de transformación de plantillas de texto personalizado, debe usar un mecanismo seguro, como el registro para el motor para localizar los procesadores de directivas.
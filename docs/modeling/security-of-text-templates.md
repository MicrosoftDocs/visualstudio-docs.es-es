---
title: Seguridad de las plantillas de texto
description: Obtenga información sobre la seguridad y las plantillas de texto, incluidos temas como código arbitrario y procesadores de directivas malintencionadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a740a6f7a4c532a61a5e412c94fa4321c5da707
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385765"
---
# <a name="security-of-text-templates"></a>Seguridad de las plantillas de texto
Las plantillas de texto tienen los siguientes problemas de seguridad:

- Las plantillas de texto son vulnerables a inserciones arbitrarias de código.

- Si el mecanismo que usa el host para buscar un procesador de directivas no es seguro, se podría ejecutar un procesador de directivas malintencionado.

## <a name="arbitrary-code"></a>Código arbitrario
 Al escribir una plantilla, puede colocar cualquier código dentro de las \<# #> etiquetas. Esto permite ejecutar código arbitrario desde dentro de una plantilla de texto.

 Asegúrese de obtener plantillas de orígenes de confianza. Asegúrese de advertir a los usuarios finales de la aplicación de que no ejecuten plantillas que no proceden de orígenes de confianza.

## <a name="malicious-directive-processor"></a>Procesador de directivas malintencionadas
 El motor de plantillas de texto interactúa con un host de transformación y uno o varios procesadores de directivas para transformar el texto de la plantilla en un archivo de salida. Para obtener más información, vea [El proceso de transformación Plantilla de texto](../modeling/the-text-template-transformation-process.md).

 Si el mecanismo que usa el host para buscar un procesador de directivas no es seguro, corre el riesgo de ejecutar un procesador de directivas malintencionado. El procesador de directivas malintencionadas podría proporcionar código que se ejecuta en `FullTrust` modo cuando se ejecuta la plantilla. Si crea un host de transformación de plantilla de texto personalizado, debe usar un mecanismo seguro, como el Registro, para que el motor busque procesadores de directivas.

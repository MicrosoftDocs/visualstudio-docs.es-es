---
title: Seguridad de las plantillas de texto
description: Obtenga información sobre seguridad y plantillas de texto, incluidos temas como código arbitrario y procesadores de directivas malintencionadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11352eb33070d3401516948cc01c4b9bd7ab4f95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893326"
---
# <a name="security-of-text-templates"></a>Seguridad de las plantillas de texto
Las plantillas de texto tienen los siguientes problemas de seguridad:

- Las plantillas de texto son vulnerables a las inserciones de código arbitrarias.

- Si el mecanismo que usa el host para buscar un procesador de directivas no es seguro, se podría ejecutar un procesador de directivas malintencionados.

## <a name="arbitrary-code"></a>Código arbitrario
 Al escribir una plantilla, puede colocar cualquier código dentro de las \<# #> etiquetas. Esto permite ejecutar código arbitrario desde una plantilla de texto.

 Asegúrese de obtener plantillas de fuentes de confianza. Asegúrese de advertir a los usuarios finales de la aplicación que no ejecuten plantillas que no provienen de orígenes de confianza.

## <a name="malicious-directive-processor"></a>Procesador de directivas malintencionadas
 El motor de plantillas de texto interactúa con un host de transformación y uno o varios procesadores de directivas para transformar el texto de la plantilla en un archivo de salida. Para obtener más información, vea [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).

 Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, corre el riesgo de ejecutar un procesador de directivas malintencionadas. El procesador de directivas malintencionadas podría proporcionar código que se ejecuta en `FullTrust` modo cuando se ejecuta la plantilla. Si crea un host de transformación de plantilla de texto personalizado, debe usar un mecanismo seguro, como el registro, para que el motor busque los procesadores de directivas.

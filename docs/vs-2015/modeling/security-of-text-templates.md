---
title: Seguridad de las plantillas de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24a90d4e7af351fc4ba5807d2af7830edede9cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671213"
---
# <a name="security-of-text-templates"></a>Seguridad de las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las plantillas de texto tienen los siguientes problemas de seguridad:

- Las plantillas de texto son vulnerables a las inserciones de código arbitrarias.

- Si el mecanismo que usa el host para buscar un procesador de directivas no es seguro, se podría ejecutar un procesador de directivas malintencionados.

## <a name="arbitrary-code"></a>Código arbitrario
 Al escribir una plantilla, puede colocar cualquier código dentro de las etiquetas \< # # >. Esto permite ejecutar código arbitrario desde una plantilla de texto.

 Asegúrese de obtener plantillas de fuentes de confianza. Asegúrese de advertir a los usuarios finales de la aplicación que no ejecuten plantillas que no provienen de orígenes de confianza.

## <a name="malicious-directive-processor"></a>Procesador de directivas malintencionadas
 El motor de plantillas de texto interactúa con un host de transformación y uno o varios procesadores de directivas para transformar el texto de la plantilla en un archivo de salida. Para obtener más información, vea [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).

 Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, corre el riesgo de ejecutar un procesador de directivas malintencionadas. El procesador de directivas malintencionadas podría proporcionar código que se ejecuta en modo `FullTrust` cuando se ejecuta la plantilla. Si crea un host de transformación de plantilla de texto personalizado, debe usar un mecanismo seguro, como el registro, para que el motor busque los procesadores de directivas.

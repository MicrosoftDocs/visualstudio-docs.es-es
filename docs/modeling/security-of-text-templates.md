---
title: Seguridad de plantillas de texto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5c6b8d64e02562887b2bc438943fdfe7be3b2e1c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="security-of-text-templates"></a>Seguridad de las plantillas de texto
Plantillas de texto tienen los siguientes problemas de seguridad:  
  
-   Plantillas de texto son vulnerables a las inserciones de código arbitrario.  
  
-   Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, se podría ejecutar un procesador de directivas malintencionado.  
  
## <a name="arbitrary-code"></a>Código arbitrario  
 Cuando se escribe una plantilla, puede colocar cualquier código dentro de la \<## > etiquetas. Esto permite al código arbitrario se ejecute desde dentro de una plantilla de texto.  
  
 Asegúrese de que obtener plantillas de orígenes de confianza. Asegúrese de que pretende advertir a los usuarios finales de su aplicación no ejecutar plantillas que no proceden de orígenes de confianza.  
  
## <a name="malicious-directive-processor"></a>Procesador de directivas malintencionado  
 El motor de plantillas de texto interactúa con un host de transformación y uno o más procesadores de directivas para transformar la plantilla de texto a un archivo de salida. Para obtener más información, consulte [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).  
  
 Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, corre el riesgo de ejecutar un procesador de directivas malintencionado. El procesador de directivas malintencionado puede proporcionar código que se ejecuta en `FullTrust` modo cuando se ejecuta la plantilla. Si crea un host de transformación de plantillas de texto personalizado, debe usar un mecanismo de seguridad, como el registro, para el motor para localizar los procesadores de directivas.
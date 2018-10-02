---
title: Seguridad de las plantillas de texto | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4ce9ccca0a144de7101e886712105315ec64fa75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567541"
---
# <a name="security-of-text-templates"></a>Seguridad de las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [seguridad de las plantillas de texto](https://docs.microsoft.com/visualstudio/modeling/security-of-text-templates).  
  
Las plantillas de texto tienen los siguientes problemas de seguridad:  
  
-   Las plantillas de texto son vulnerables a las inserciones de código arbitrario.  
  
-   Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, se podría ejecutar un procesador de directivas malintencionado.  
  
## <a name="arbitrary-code"></a>Código arbitrario  
 Al escribir una plantilla, puede colocar cualquier código dentro de la \<## > etiquetas. Esto permite que el código arbitrario para ejecutarse desde una plantilla de texto.  
  
 Asegúrese de que obtener las plantillas de orígenes de confianza. Asegúrese de que advertir a los usuarios finales de su aplicación no ejecutar plantillas que no procedan de fuentes de confianza.  
  
## <a name="malicious-directive-processor"></a>Procesador de directivas malintencionado  
 El motor de plantillas de texto interactúa con un host de transformación y uno o más procesadores de directivas para transformar el texto de la plantilla en un archivo de salida. Para obtener más información, consulte [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).  
  
 Si el mecanismo que usa el host para encontrar un procesador de directivas no es seguro, se corre el riesgo de la ejecución de un procesador de directivas malintencionado. El procesador de directivas malintencionado podría proporcionar código que se ejecuta en `FullTrust` modo cuando se ejecuta la plantilla. Si crea un host de transformación de plantillas de texto personalizado, debe usar un mecanismo seguro, como el registro para el motor para localizar los procesadores de directivas.




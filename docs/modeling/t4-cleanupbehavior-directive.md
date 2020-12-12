---
title: T4 CleanUpBehavior (Directiva)
description: Obtenga información sobre la Directiva CleanUpBehavior y cómo eliminar el appDomain después de procesar una plantilla de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c07d0bf714d42cc605d76d593ed48a70b925483
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363684"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior (Directiva)

Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host. En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente. Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.

Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.

Esta directiva solo funciona en el host de Visual Studio.

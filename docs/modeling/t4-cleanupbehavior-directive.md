---
title: T4 CleanUpBehavior (Directiva)
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da296be872daa89d2759566020452fab4951d3b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606491"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior (Directiva)

Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host. En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente. Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.

Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.

Esta directiva solo funciona en el host de Visual Studio.
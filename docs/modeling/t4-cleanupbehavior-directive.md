---
title: T4 CleanUpBehavior (Directiva)
description: Obtenga información sobre la Directiva CleanUpBehavior y cómo eliminar el appDomain después de procesar una plantilla de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49609dd13e2e322f88f265d27e55c49154f4c5c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899648"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior (Directiva)

Para eliminar el objeto appDomain después de procesar una plantilla de texto, incluya la línea siguiente:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Las plantillas de texto se procesan en un objeto appDomain que es independiente del proceso host. En la mayoría de los casos, cuando se ha procesado una plantilla de texto, el objeto appdomain se utiliza de nuevo para procesar la plantilla siguiente. Sin embargo, si especifica CleanupBehavior, el objeto appDomain se elimina y la plantilla siguiente se procesará en un nuevo objeto appDomain.

Esto reduce el procesamiento de texto, pero puede ser útil para garantizar que se desechan los recursos.

Esta directiva solo funciona en el host de Visual Studio.

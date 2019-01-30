---
title: Procedimientos recomendados de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 622d7b087e94d21f86691b88c3af4891aa533e9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013215"
---
# <a name="msbuild-best-practices"></a>Procedimientos recomendados de MSBuild
Le recomendamos los siguientes procedimientos para escribir scripts de MSBuild:  
  
-   Los valores de propiedad predeterminados se controlan mejor mediante el uso del atributo `Condition` sin declarar una propiedad cuyo valor predeterminado se puede reemplazar en la línea de comandos. Por ejemplo, use  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   Evite los caracteres comodín cuando seleccione elementos. En su lugar, especifique los archivos explícitamente. Esto hace más fácil realizar un seguimiento de los errores que pueden producirse al agregar o eliminar archivos.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)

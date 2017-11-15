---
title: Procedimientos recomendados de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 881075ee32ccac155237035dbe1a2f6d17a82893
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-best-practices"></a>Procedimientos recomendados de MSBuild
Le recomendamos los siguientes procedimientos para escribir scripts de MSBuild:  
  
-   Los valores de propiedad predeterminados se controlan mejor mediante el uso del atributo `Condition` sin declarar una propiedad cuyo valor predeterminado se puede reemplazar en la línea de comandos. Por ejemplo, use  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evite los caracteres comodín cuando seleccione elementos. En su lugar, especifique los archivos explícitamente. Esto hace más fácil realizar un seguimiento de los errores que pueden producirse al agregar o eliminar archivos.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)

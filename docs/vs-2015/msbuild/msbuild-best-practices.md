---
title: Procedimientos recomendados de MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6973e905a0587ffdc7cbd0a401e03f933fc60a3a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662224"
---
# <a name="msbuild-best-practices"></a>Procedimientos recomendados de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le recomendamos los siguientes procedimientos para escribir scripts de MSBuild:  
  
-   Los valores de propiedad predeterminados se controlan mejor mediante el uso del atributo `Condition` sin declarar una propiedad cuyo valor predeterminado se puede reemplazar en la línea de comandos. Por ejemplo, use  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evite los caracteres comodín cuando seleccione elementos. En su lugar, especifique los archivos explícitamente. Esto hace más fácil realizar un seguimiento de los errores que pueden producirse al agregar o eliminar archivos.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)

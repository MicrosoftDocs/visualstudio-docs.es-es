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
ms.openlocfilehash: ad2070bb696a3ce326331d01145b3ef3b54ae5ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780671"
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

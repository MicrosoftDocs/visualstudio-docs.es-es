---
title: Referencia circular en un argumento de valor no admitida | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349080"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Referencia circular en un argumento de valor no admitida
Se ha intentado invocar `JSON.stringify` con un valor que no es válido. El `value` argumento, matriz u objeto, contiene una referencia circular.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quite el argumento de la referencia circular.  
  
## <a name="example"></a>Ejemplo  
 El código en este ejemplo genera un error de tiempo de ejecución porque `john` tiene una referencia a `mary` y `mary` tiene una referencia a `john`. Para quitar la referencia circular, quitar o desactivar la propiedad `brother` desde el `mary` objeto o la `sister` propiedad desde la `john` objeto.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Vea también  
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)
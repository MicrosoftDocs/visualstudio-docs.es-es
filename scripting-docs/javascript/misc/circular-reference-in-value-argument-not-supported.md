---
title: Referencia circular en el argumento de valor no admitida | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817624"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Referencia circular en el argumento de valor no admitida
Se ha intentado invocar `JSON.stringify` con un valor que no es válido. El `value` argumento, una matriz o un objeto, contiene una referencia circular.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quite la referencia circular del argumento.  
  
## <a name="example"></a>Ejemplo  
 El código de este ejemplo produce un error en tiempo de ejecución porque `john` tiene una referencia a `mary` y `mary` tiene una referencia a `john` . para quitar la referencia circular, quite o anule la propiedad del `brother` `mary` objeto o la `sister` propiedad del `john` objeto.  
  
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
 [JSON. Parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)
---
title: Referencia circular en el argumento de valor no admitida | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572338"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Referencia circular en el argumento de valor no admitida
Se ha intentado invocar `JSON.stringify` con un valor que no es válido. El argumento `value`, una matriz o un objeto, contiene una referencia circular.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quite la referencia circular del argumento.  
  
## <a name="example"></a>Ejemplo  
 El código de este ejemplo produce un error en tiempo de ejecución porque `john` tiene una referencia a `mary` y `mary` tiene una referencia a `john`. para quitar la referencia circular, quite o anule la propiedad `brother` del objeto `mary` o la propiedad `sister` del objeto `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de [objeto JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 de la [función JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)
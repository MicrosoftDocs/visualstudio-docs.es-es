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
ms.openlocfilehash: aa753a4ba3e0254ed7de026653759bbdcfce0631
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862316"
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
 [Objeto JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse (función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Errores en tiempo de ejecución de JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
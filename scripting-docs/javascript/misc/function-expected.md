---
description: Se intentó invocar uno de los métodos de prototipo de función en un objeto que no era un objeto de función o se usó un objeto en un contexto de llamada de función.
title: Función esperada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99e354118844d7e57f708cf3f2d5653ee1c0fc65
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622613"
---
# <a name="function-expected"></a>Se esperaba una función
Intentó invocar uno de los métodos de **prototipo de función** en un objeto que no era un `Function` objeto o usó un objeto en un contexto de llamada de función. Por ejemplo, el código siguiente genera este error porque el **ejemplo** no es una función.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se llama a los métodos de **prototipo de función** en `Function` objetos.  
  
- Asegúrese de usar el operador de llamada de función `()` para llamar solo a funciones.  
  
## <a name="see-also"></a>Consulte también  
 [Objeto de función](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype (Propiedad, Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)

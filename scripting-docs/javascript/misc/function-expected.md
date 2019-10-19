---
title: Función esperada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576593"
---
# <a name="function-expected"></a>Se esperaba una función
Se intentó invocar uno de los métodos de **prototipo de función** en un objeto que no era un objeto `Function`, o se usó un objeto en un contexto de llamada de función. Por ejemplo, el código siguiente genera este error porque el **ejemplo** no es una función.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se llama a los métodos de **prototipo de función** en objetos `Function`.  
  
- Asegúrese de usar el operador de llamada de función `()` para llamar solo a funciones.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)    
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)
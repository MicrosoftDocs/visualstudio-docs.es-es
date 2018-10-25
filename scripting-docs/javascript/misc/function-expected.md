---
title: Se esperaba una función | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928937"
---
# <a name="function-expected"></a>Se esperaba una función
O bien ha intentado invocar a uno de los **prototipo de función** métodos en un objeto que no era un `Function` objeto, o usar un objeto en un contexto de llamada de función. Por ejemplo, el código siguiente provoca este error porque **ejemplo** no es una función.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Solo llame a **prototipo de función** métodos en `Function` objetos.  
  
-   Asegúrese de que usa el operador de llamada de función `()` para llamar a funciones solamente.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)
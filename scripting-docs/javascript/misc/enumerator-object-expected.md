---
title: Se esperaba un objeto de enumerador | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946347"
---
# <a name="enumerator-object-expected"></a>Se esperaba un objeto enumerador
Se intentó invocar el **método Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** o **Enumerator.prototype.moveNext** método en un objeto de un tipo que `Enumerator`. El objeto de este tipo de invocación debe ser de tipo `Enumerator`. Este es un ejemplo de código que infringe esta regla:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invoque la **método Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, o  **Enumerator.prototype.moveNext** métodos en objetos de tipo `Enumerator`. Para averiguar si el objeto es un `Enumerator` de objeto, use:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Enumerator (Objeto)](../../javascript/reference/enumerator-object-javascript.md)
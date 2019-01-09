---
title: Se esperaba un objeto de enumerador | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 002c3a748af8f7fa5c21109adcb279f893b38965
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093007"
---
# <a name="enumerator-object-expected"></a>Se esperaba un objeto enumerador
Se intentó invocar el **método Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** o **Enumerator.prototype.moveNext** método en un objeto de un tipo que `Enumerator`. El objeto de este tipo de invocación debe ser de tipo `Enumerator`. Este es un ejemplo de código que infringe esta regla:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Solo se invoque la **método Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, o  **Enumerator.prototype.moveNext** métodos en objetos de tipo `Enumerator`. Para averiguar si el objeto es un `Enumerator` de objeto, use:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Enumerator (Objeto)](../../javascript/reference/enumerator-object-javascript.md)
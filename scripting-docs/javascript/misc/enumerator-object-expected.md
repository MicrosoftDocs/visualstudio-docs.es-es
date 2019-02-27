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
ms.openlocfilehash: 14fcb4d990b03a8e7b896014403eb8dceac66b80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841836"
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
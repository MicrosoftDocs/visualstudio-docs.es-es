---
title: Se esperaba un objeto enumerador | Microsoft Docs
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572869"
---
# <a name="enumerator-object-expected"></a>Se esperaba un objeto enumerador
Intentó invocar el método **enumerador. prototype. Atend (, Enumerator. prototype. Item, Enumerator. prototype. moveFirst** o **Enumerator. prototype. MoveNext** en un objeto de un tipo distinto de `Enumerator`. El objeto de este tipo de invocación debe ser de tipo `Enumerator`. Este es un ejemplo de código que interrumpe esta regla:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **Enumerator. prototype. Atend (** , **Enumerator. prototype. Item**, **Enumerator. prototype. moveFirst**o **Enumerator. prototype. MoveNext** en objetos de tipo `Enumerator`. Para averiguar si el objeto es un objeto `Enumerator`, use:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Enumerator (objeto)](../../javascript/reference/enumerator-object-javascript.md)
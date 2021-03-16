---
description: Intentó invocar el método enumerador. prototype. Atend (, Enumerator. prototype. Item, Enumerator. prototype. moveFirst o Enumerator. prototype. moveNext en un objeto de un tipo que no sea un enumerador.
title: Se esperaba un objeto enumerador | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571056"
---
# <a name="enumerator-object-expected"></a>Se esperaba un objeto enumerador
Intentó invocar el método **enumerador. prototype. Atend (, Enumerator. prototype. Item, Enumerator. prototype. moveFirst** o **Enumerator. prototype. MoveNext** en un objeto de un tipo distinto de `Enumerator` . El objeto de este tipo de invocación debe ser de tipo `Enumerator` . Este es un ejemplo de código que interrumpe esta regla:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **Enumerator. prototype. Atend (**, **Enumerator. prototype. Item**, **Enumerator. prototype. moveFirst** o **Enumerator. prototype. MoveNext** en objetos de tipo `Enumerator` . Para averiguar si el objeto es un `Enumerator` objeto, use:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Enumerator (Objeto)](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)

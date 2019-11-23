---
title: Se esperaba un objeto de fecha | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572901"
---
# <a name="date-object-expected"></a>Se esperaba un objeto de fecha
Intentó invocar el método **Date. prototype. ToString** o **Date. prototype.** typeof en un objeto de un tipo distinto de `Date`. El objeto de este tipo de invocación debe ser de tipo `Date`. Por ejemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **Date. prototype. ToString** o **Date. prototype. valueto** en objetos de tipo `Date`.  
  
## <a name="see-also"></a>Vea también  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [getDate (método, Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)
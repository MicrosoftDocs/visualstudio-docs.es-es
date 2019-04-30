---
title: Se esperaba un objeto de fecha | Documentos de Microsoft
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
ms.openlocfilehash: 2767ffc16b637c6b1e7bdf51cb0815d71f58edac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946386"
---
# <a name="date-object-expected"></a>Se esperaba un objeto de fecha
Se intentó invocar el **Date.prototype.toString** o **Date.prototype.valueOf** método en un objeto de un tipo distinto `Date`. El objeto de este tipo de invocación debe ser de tipo `Date`. Por ejemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invoque la **Date.prototype.toString** o **Date.prototype.valueOf** métodos en objetos de tipo `Date`.  
  
## <a name="see-also"></a>Vea también  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [getDate (método) (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)
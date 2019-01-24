---
title: Se esperaba un objeto de fecha | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349119"
---
# <a name="date-object-expected"></a>Se esperaba un objeto de fecha
Se intentó invocar el **Date.prototype.toString** o **Date.prototype.valueOf** método en un objeto de un tipo distinto `Date`. El objeto de este tipo de invocación debe ser de tipo `Date`. Por ejemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Solo se invoque la **Date.prototype.toString** o **Date.prototype.valueOf** métodos en objetos de tipo `Date`.  
  
## <a name="see-also"></a>Vea también  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [getDate (método) (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)
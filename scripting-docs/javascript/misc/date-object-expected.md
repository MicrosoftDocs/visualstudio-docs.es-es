---
description: Intentó invocar el método Date. prototype. toString o Date. prototype. valueto en un objeto de un tipo que no es Date.
title: Se esperaba un objeto de fecha | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 171514ae180c2e9b24e8aee56a23c47a909bd152
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571095"
---
# <a name="date-object-expected"></a>Se esperaba un objeto de fecha
Intentó invocar el método **Date. prototype. ToString** o **Date. prototype. valueto** en un objeto de un tipo distinto de `Date` . El objeto de este tipo de invocación debe ser de tipo `Date` . Por ejemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **Date. prototype. ToString** o **Date. prototype. valueto** en objetos de tipo `Date` .  
  
## <a name="see-also"></a>Consulte también  
 [Date (objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [getDate (método, Date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Objetos intrínsecos](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)

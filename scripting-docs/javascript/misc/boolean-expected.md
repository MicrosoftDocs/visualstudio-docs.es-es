---
title: Se esperaba un booleano | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Se esperaba un tipo booleano
Se intentó invocar el **Boolean.prototype.toString** o **Boolean.prototype.valueOf** método en un objeto de un tipo distinto de `Boolean`. El objeto de este tipo de invocación debe ser de tipo `Boolean`. Por ejemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Invocar solo el valor booleano**. prototype.toString** o **Boolean.prototype.valueOf** métodos en objetos de tipo **booleano.**  
  
## <a name="see-also"></a>Vea también  
 [Boolean (objeto)](../../javascript/reference/boolean-object-javascript.md)   
 [Tipos de datos](../../javascript/data-types-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Copia, pase y comparación de datos](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)
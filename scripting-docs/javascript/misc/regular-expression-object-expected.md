---
title: "Se esperaba un objeto de expresión regular | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a5a0f3cb3b86e2e01d522f85d0dae23e9c9d3ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-expected"></a>Se esperaba un objeto de expresión regular
Se intentó invocar el **RegExp.prototype.toString** o **RegExp.prototype.valueOf** método en un objeto de un tipo distinto de `RegExp`. El objeto de este tipo de invocación debe ser de tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Solo se invoque el **RegExp.prototype.toString** o **RegExp.prototype.valueOf** métodos en objetos de tipo `RegExp`.  
  
## <a name="see-also"></a>Vea también  
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)
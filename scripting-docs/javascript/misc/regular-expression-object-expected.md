---
title: Se esperaba un objeto de expresión regular | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a42cf4b76f4de6d4170f7ef85dafc00841964cfc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064909"
---
# <a name="regular-expression-object-expected"></a>Se esperaba un objeto de expresión regular
Se intentó invocar el **RegExp.prototype.toString** o **RegExp.prototype.valueOf** método en un objeto de un tipo distinto `RegExp`. El objeto de este tipo de invocación debe ser de tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invoque la **RegExp.prototype.toString** o **RegExp.prototype.valueOf** métodos en objetos de tipo `RegExp`.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)
---
title: Se esperaba un objeto de expresión regular | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8e3c48b116680fe73d4cc318038cb2c13c4164
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280321"
---
# <a name="regular-expression-object-expected"></a>Se esperaba un objeto de expresión regular
Se intentó invocar el **RegExp.prototype.toString** o **RegExp.prototype.valueOf** método en un objeto de un tipo distinto `RegExp`. El objeto de este tipo de invocación debe ser de tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Solo se invoque la **RegExp.prototype.toString** o **RegExp.prototype.valueOf** métodos en objetos de tipo `RegExp`.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)
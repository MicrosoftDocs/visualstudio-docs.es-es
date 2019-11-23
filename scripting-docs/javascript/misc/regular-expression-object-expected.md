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
ms.openlocfilehash: bf9e2e99c6a539f450afcfe9eef1f5588d5b84f6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573705"
---
# <a name="regular-expression-object-expected"></a>Se esperaba un objeto de expresión regular
Intentó invocar el método **RegExp. prototype. ToString** o **RegExp. prototype.** typeof en un objeto de un tipo distinto de `RegExp`. El objeto de este tipo de invocación debe ser de tipo `RegExp`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **RegExp. prototype. ToString** o **RegExp. prototype. valueto** en objetos de tipo `RegExp`.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión Regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresiones regulares (JavaScript)](https://msdn.microsoft.com/library/1400241x)
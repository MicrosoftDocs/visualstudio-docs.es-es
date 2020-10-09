---
title: Se esperaba un objeto de expresión regular | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 370e5a8028bae0e60c265ba65dca12668e4b8d8c
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862059"
---
# <a name="regular-expression-object-expected"></a>Se esperaba un objeto de expresión regular
Intentó invocar el método **RegExp. prototype. ToString** o **RegExp. prototype. valueto** en un objeto de un tipo distinto de `RegExp` . El objeto de este tipo de invocación debe ser de tipo `RegExp` .  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **RegExp. prototype. ToString** o **RegExp. prototype. valueto** en objetos de tipo `RegExp` .  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxis de expresiones regulares (JavaScript)](/previous-versions/1400241x(v=vs.100))
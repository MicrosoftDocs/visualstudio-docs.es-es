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
ms.openlocfilehash: d9f5816c0bf3ad7c8dbf7d394952c631923d89cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814634"
---
# <a name="regular-expression-object-expected"></a>Se esperaba un objeto de expresión regular
Intentó invocar el método **RegExp. prototype. ToString** o **RegExp. prototype. valueto** en un objeto de un tipo distinto de `RegExp` . El objeto de este tipo de invocación debe ser de tipo `RegExp` .  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Solo se invocan los métodos **RegExp. prototype. ToString** o **RegExp. prototype. valueto** en objetos de tipo `RegExp` .  
  
## <a name="see-also"></a>Consulte también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresiones regulares (JavaScript)](https://msdn.microsoft.com/library/1400241x)
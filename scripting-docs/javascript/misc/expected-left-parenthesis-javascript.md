---
title: Se esperaba ' (' (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adcabbe0b1d7ca7d0298202b5242049b86f8229a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817104"
---
# <a name="expected--javascript"></a>Se esperaba '(' (JavaScript)
Intentó incluir una expresión dentro de un conjunto de paréntesis, pero no incluía el paréntesis de apertura. Algunas expresiones se deben incluir en un conjunto de paréntesis de apertura y cierre. Observe el uso de paréntesis en el ejemplo siguiente.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue el paréntesis izquierdo a la expresión de evaluación.
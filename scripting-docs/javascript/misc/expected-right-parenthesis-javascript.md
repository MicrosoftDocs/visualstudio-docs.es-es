---
title: Se esperaba ')' (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2fb72012-0f83-40fa-b747-167940d90bdd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f6a0128bb73e69a151415518ae6c019be0e4df9
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804674"
---
# <a name="expected--javascript"></a>Se esperaba ')' (JavaScript)
Se intentó incluir una expresión dentro de un conjunto de paréntesis, pero no incluía el paréntesis de cierre. Alguna expresión debe incluirse dentro de un conjunto de apertura y cierre entre paréntesis. Tenga en cuenta el uso de paréntesis en el ejemplo siguiente.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el paréntesis de cierre a la expresión de evaluación.
---
title: Se esperaba '(' (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cf1f092e91079c6f052fd07b40f276d04332b2f
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348274"
---
# <a name="expected--javascript"></a>Se esperaba '(' (JavaScript)
Se intentó incluir una expresión dentro de un conjunto de paréntesis, pero no incluía el paréntesis de apertura. Algunas expresiones deben encerrarse entre un conjunto de apertura y cierre entre paréntesis. Tenga en cuenta el uso de paréntesis en el ejemplo siguiente.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el paréntesis de apertura para la expresión de evaluación.
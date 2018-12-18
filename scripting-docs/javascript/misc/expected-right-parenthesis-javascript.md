---
title: Se esperaba &#39;)&#39; (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: f816b4635ae219b12370d53fa8c14eb8c0112a7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863547"
---
# <a name="expected-3939-javascript"></a>Se esperaba &#39;)&#39; (JavaScript)
Se intentó incluir una expresión dentro de un conjunto de paréntesis, pero no incluía el paréntesis de cierre. Alguna expresión debe incluirse dentro de un conjunto de apertura y cierre entre paréntesis. Tenga en cuenta el uso de paréntesis en el ejemplo siguiente.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el paréntesis de cierre a la expresión de evaluación.
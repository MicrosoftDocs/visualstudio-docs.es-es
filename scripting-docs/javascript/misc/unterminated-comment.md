---
title: Comentario sin terminar | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8453b05d2d09537f381bd2947dccb6b0a19a6263
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861835"
---
# <a name="unterminated-comment"></a>Comentario sin terminar
Comenzó un bloque de comentarios de varias líneas, pero no lo terminó correctamente. Los comentarios de varias líneas comienzan con una combinación "/*" y terminan con la combinación inversa " \* /". Este es un ejemplo:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de terminar los comentarios de varias líneas con "*/".  
  
## <a name="see-also"></a>Vea también  
 [Comment (Instrucciones)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)
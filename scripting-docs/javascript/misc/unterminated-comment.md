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
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814808"
---
# <a name="unterminated-comment"></a>Comentario sin terminar
Comenzó un bloque de comentarios de varias líneas, pero no lo terminó correctamente. Los comentarios de varias líneas comienzan con una combinación "/*" y terminan con la combinación inversa " \* /". A continuación se muestra un ejemplo:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de terminar los comentarios de varias líneas con "*/".  
  
## <a name="see-also"></a>Vea también  
 [Comment (Instrucciones)](../../javascript/reference/comment-statements-javascript.md)
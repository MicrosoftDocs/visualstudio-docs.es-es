---
title: Sin terminar comentario | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: f2b21c585bb48b55929a78554d686477e0fa5649
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842453"
---
# <a name="unterminated-comment"></a>Comentario sin terminar
Se inició un bloque de comentario de varias líneas, pero no correctamente finalizó. Comentarios de varias líneas que comienzan por un "/\*" combinación y terminan con la inversa "\*/" combinación. A continuación se muestra un ejemplo:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de terminar los comentarios de varias líneas con "*/".  
  
## <a name="see-also"></a>Vea también  
 [Comment (Instrucciones)](../../javascript/reference/comment-statements-javascript.md)
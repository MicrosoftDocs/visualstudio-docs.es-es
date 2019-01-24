---
title: Sin terminar comentario | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fde5d5edd7e81060b088e4940d752aa05e65ded
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348189"
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
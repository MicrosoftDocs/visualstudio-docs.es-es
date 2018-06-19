---
title: toGMTString (método, Date) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640115"
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString (Método, Date de JavaScript)
Devuelve una fecha convertida en una cadena con la hora del meridiano significa (GMT).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `dateObj` referencia es cualquier `Date` objeto.  
  
 El `toGMTString` método está obsoleto y se proporciona la compatibilidad con versiones anteriores. Se recomienda que use la `toUTCString` método en su lugar.  
  
 El `toGMTString` método devuelve un `String` objeto que contiene la fecha con formato con la convención de GMT. El formato del valor devuelto es el siguiente: "05 de Jan de 1996 00:00:00 GMT".  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toUTCString (Método, Date)](../../javascript/reference/toutcstring-method-date-javascript.md)
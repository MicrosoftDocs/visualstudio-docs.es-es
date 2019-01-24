---
title: Se esperaba VBArray | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4b5416c6e37e59a60206bd21606b5214f05a269
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347468"
---
# <a name="vbarray-expected"></a>Se esperaba VBArray
Proporciona un objeto que no era un safeArray de Visual Basic, cuando se esperaba uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Los elementos VBArray son de solo lectura y no se pueden crear directamente. El argumento safeArray es un valor VBArray y debe haber obtenido un valor VBArray antes de que se pasan a la `VBArray` constructor. Esto solo se puede hacer si se recupera el valor de un objeto ActiveX u otro existente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que pase solo **VBArray** objetos a la **VBArray** constructor.  
  
## <a name="see-also"></a>Vea también  
 [VBArray (objeto)](../../javascript/reference/vbarray-object-javascript.md)   
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)
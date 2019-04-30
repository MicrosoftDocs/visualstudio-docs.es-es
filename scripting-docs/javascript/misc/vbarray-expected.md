---
title: Se esperaba VBArray | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005997"
---
# <a name="vbarray-expected"></a>Se esperaba VBArray
Proporciona un objeto que no era un safeArray de Visual Basic, cuando se esperaba uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Los elementos VBArray son de solo lectura y no se pueden crear directamente. El argumento safeArray es un valor VBArray y debe haber obtenido un valor VBArray antes de que se pasan a la `VBArray` constructor. Esto solo se puede hacer si se recupera el valor de un objeto ActiveX u otro existente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que pase solo **VBArray** objetos a la **VBArray** constructor.  
  
## <a name="see-also"></a>Vea también  
 [VBArray (objeto)](../../javascript/reference/vbarray-object-javascript.md)   
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)
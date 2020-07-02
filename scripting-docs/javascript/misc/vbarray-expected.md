---
title: Se esperaba VBArray | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 09ab257e6c473e2747a24559200e7b1f432d5687
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815284"
---
# <a name="vbarray-expected"></a>Se esperaba VBArray
Proporcionó un objeto que no era un Visual Basic safeArray, cuando se esperaba uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Los elementos VBArray son de solo lectura y no se pueden crear directamente. El argumento safeArray es un valor VBArray y debe haber obtenido un valor VBArray antes de pasarse al `VBArray` constructor. Esto solo se puede hacer si se recupera el valor de un objeto ActiveX u otro existente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de pasar solo objetos **VBArray** al constructor **VBArray** .  
  
## <a name="see-also"></a>Vea también  
 [VBArray (objeto)](../../javascript/reference/vbarray-object-javascript.md)   
 [Usar matrices](../../javascript/advanced/using-arrays-javascript.md)
---
description: Proporcionó un objeto que no era un Visual Basic safeArray, cuando se esperaba uno.
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
ms.openlocfilehash: e344e24b3fbef7b7f119a36513c222e085328072
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572083"
---
# <a name="vbarray-expected"></a>Se esperaba VBArray
Proporcionó un objeto que no era un Visual Basic safeArray, cuando se esperaba uno.  
  
```js
new VBArray(safeArray);  
```  
  
 Los elementos VBArray son de solo lectura y no se pueden crear directamente. El argumento safeArray es un valor VBArray y debe haber obtenido un valor VBArray antes de pasarse al `VBArray` constructor. Esto solo se puede hacer si se recupera el valor de un objeto ActiveX u otro existente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de pasar solo objetos **VBArray** al constructor **VBArray** .  
  
## <a name="see-also"></a>Consulte también  
 [VBArray (objeto)](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Usar matrices](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)

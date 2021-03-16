---
description: Intentó usar la palabra clave break fuera de un bucle.
title: No se puede tener ' break ' fuera del bucle | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570653"
---
# <a name="cant-have-break-outside-of-loop"></a>'break' no puede estar fuera del bucle
Intentó usar la palabra clave **break** fuera de un bucle. La palabra clave **break** se usa para terminar un bucle o una `switch` instrucción. Debe estar incrustado en el cuerpo de un bucle o `switch` instrucción. Sin embargo, una **etiqueta** puede seguir a la palabra clave break.  
  
```js
break labelname;  
```  
  
 Solo se necesita el formulario con etiqueta de la palabra clave **break** cuando se usan instrucciones o bucles anidados `switch` y es necesario interrumpir un bucle que no sea el más interno.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la palabra clave **break** aparece dentro de un bucle envolvente o una instrucción switch.  
  
## <a name="see-also"></a>Consulte también  
 [Break (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Controlar el flujo del programa](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Solución de problemas de los scripts](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)

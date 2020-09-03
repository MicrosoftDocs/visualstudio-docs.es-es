---
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
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817663"
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
 [Break (instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solución de problemas de los scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
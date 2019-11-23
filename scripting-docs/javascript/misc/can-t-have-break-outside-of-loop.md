---
title: No se puede tener ' break ' fuera del bucle | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576016"
---
# <a name="cant-have-break-outside-of-loop"></a>'break' no puede estar fuera del bucle
Intentó usar la palabra clave **break** fuera de un bucle. La palabra clave **break** se usa para terminar un bucle o una instrucción `switch`. Debe estar incrustado en el cuerpo de un bucle o una instrucción `switch`. Sin embargo, una **etiqueta** puede seguir a la palabra clave break.  
  
```js
break labelname;  
```  
  
 Solo se necesita el formulario con etiqueta de la palabra clave **break** cuando se usan bucles anidados o instrucciones `switch` y es necesario interrumpir un bucle que no sea el más interno.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la palabra clave **break** aparece dentro de un bucle envolvente o una instrucción switch.  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solución de problemas de los scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
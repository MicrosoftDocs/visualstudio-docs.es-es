---
title: No puede tener 'break' fuera del bucle | Microsoft Docs
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
ms.openlocfilehash: 36551a1a70973409768b7971545c783b3621ffb6
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839898"
---
# <a name="cant-have-break-outside-of-loop"></a>'break' no puede estar fuera del bucle
Se intentó utilizar el **salto** palabra clave fuera de un bucle. El **salto** palabra clave se usa para finalizar un bucle o `switch` instrucción. Se debe incrustar en el cuerpo de un bucle o `switch` instrucción. Sin embargo, un **etiqueta** puede seguir la palabra clave break.  
  
```js
break labelname;  
```  
  
 Solo necesita el formulario con la etiqueta de la **salto** palabra clave cuando se usa bucles anidados o `switch` instrucciones y la necesidad de interrumpir un bucle que no es el más interno.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que el **salto** palabra clave aparece dentro de una instrucción de bucle o switch envolvente.  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solución de problemas de los scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
---
title: Puede&#39;t tiene &#39;salto&#39; fuera del bucle | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928560"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Puede&#39;t tiene &#39;salto&#39; fuera del bucle
Se intentó utilizar el **salto** palabra clave fuera de un bucle. El **salto** palabra clave se usa para finalizar un bucle o `switch` instrucción. Se debe incrustar en el cuerpo de un bucle o `switch` instrucción. Sin embargo, un **etiqueta** puede seguir la palabra clave break.  
  
```  
break labelname;  
```  
  
 Solo necesita el formulario con la etiqueta de la **salto** palabra clave cuando se usa bucles anidados o `switch` instrucciones y la necesidad de interrumpir un bucle que no es el más interno.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que el **salto** palabra clave aparece dentro de una instrucción de bucle o switch envolvente.  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solución de problemas de los scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
---
title: No se puede asignar a &#39; esto &#39; | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>No se puede asignar a &#39; esto &#39;
Se intentó asignar un valor a **esto**. **Esto** es un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palabra clave que hace referencia a uno:  
  
-   el objeto que se está ejecutando actualmente un método  
  
-   el objeto global, si no hay ningún método actual (o el método no pertenece a ningún otro objeto).  
  
 Un método es un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] función que se invoca a través de un objeto. Dentro de un método, el **esto** palabra clave es una referencia al objeto se ha invocado el método mediante (que resulta ser el objeto que se crea mediante una llamada al constructor de clase con la **nueva** operador).  
  
 Dentro de un método, puede usar **esto** hacer referencia al objeto actual, pero no puede asignar un nuevo valor a **esto**.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   No intente asignar a **esto**. Para obtener acceso a una propiedad o método de un objeto con instancias, utilice el operador punto (p. ej., circle**.** RADIUS).  
  
    > [!NOTE]
    >  No se asigne un nombre a una variable creada por el usuario **esto**; es un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palabra reservada.  
  
## <a name="see-also"></a>Vea también  
 [Esta instrucción](../../javascript/reference/this-statement-javascript.md)   
 [Solución de problemas de los scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
---
title: Compilación condicional está desactiva | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633115"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilación condicional está desactiva
Se intentó utilizar una variable de compilación condicional sin primero activar la compilación condicional en. Activar la compilación condicional indica la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilador que interprete los identificadores que empiezan con @ como variables de compilación condicional. Para ello, empiece el código condicional con la instrucción:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue la siguiente instrucción al principio del código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstrucción](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifInstrucción](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instrucción](../../javascript/reference/at-set-statement-javascript.md)
---
title: La etiqueta de instrucción (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637605"
---
# <a name="labeled-statement-javascript"></a>Labeled (Instrucción de JavaScript)
Proporciona un identificador para una instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Parámetros  
 *etiqueta*  
 Obligatorio. Un identificador único que se usa al hacer referencia a la instrucción con etiqueta.  
  
 `statements`  
 Opcional. Una o varias instrucciones asociadas con *etiqueta*.  
  
## <a name="remarks"></a>Comentarios  
 Las etiquetas se utilizan por la **salto** y **continuar** instrucciones para especificar la instrucción a la que el **salto** y **continuar** aplicar.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente, la **continuar** instrucción hace referencia a la **para** bucle que va precedido por el `Inner:` instrucción. Cuando `j` es 24, el **continuar** instrucción hace que **para** bucle para ir a la siguiente iteración. Imprimirán los números de 21 a 23 y 25 a 30 en cada línea.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [continue (Instrucción)](../../javascript/reference/continue-statement-javascript.md)
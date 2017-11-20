---
title: Longitud de la matriz debe ser un entero positivo finito | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La longitud de la matriz debe ser un valor entero positivo finito
Se está llamando a la **matriz** constructor con un argumento que no es un número entero (números enteros constan de cero y el conjunto de números enteros positivos).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Utilizar enteros positivos sólo cuando se crea un nuevo `Array` objeto. Si desea crear una matriz con un único elemento que no es un entero, puede hacerlo en un proceso de dos pasos. Crear una matriz con un elemento y después coloque el valor en el primer elemento (array[0]). El siguiente es un ejemplo que genera este error.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     En el ejemplo siguiente se muestra la forma correcta para especificar una matriz con un solo elemento numérico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     No hay ningún límite superior para el tamaño de una matriz, que no sea el valor entero máximo (aproximadamente 4 mil millones).  
  
## <a name="see-also"></a>Vea también  
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)
---
title: La longitud de la matriz debe ser un entero positivo finito | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0b827e0cef5cd6c6ea4aeaddc9f32f02004c214
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862219"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La longitud de la matriz debe ser un entero positivo finito
Está llamando al constructor de **matriz** con un argumento que no es un número entero (los números enteros están compuestos de cero más el conjunto de enteros positivos).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Use enteros positivos solo al crear un nuevo `Array` objeto. Si desea crear una matriz con un solo elemento que no sea un entero, hágalo en un proceso de dos pasos. En primer lugar, cree una matriz con un elemento y, a continuación, coloque el valor en el primer elemento (array [0]). El siguiente es un ejemplo que genera este error.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     En el ejemplo siguiente se muestra la manera correcta de especificar una matriz con un solo elemento numérico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     No hay ningún límite superior para el tamaño de una matriz, excepto el valor entero máximo (aproximadamente 4 mil millones).  
  
## <a name="see-also"></a>Vea también  
 [Usar matrices](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
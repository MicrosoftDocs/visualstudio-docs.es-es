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
ms.openlocfilehash: fa8b9a85c0c7457cb06d36fd3cd849ce48484b46
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817091"
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
 [Usar matrices](../../javascript/advanced/using-arrays-javascript.md)
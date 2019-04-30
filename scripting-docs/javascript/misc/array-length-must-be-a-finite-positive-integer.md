---
title: Longitud de la matriz debe ser un entero positivo finito | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 31673205a7ca94783985e0249c5664b4bbca6147
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818129"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La longitud de la matriz debe ser un entero positivo finito
Se está llamando a la **matriz** constructor con un argumento que no es un número entero (números enteros constan de cero y el conjunto de números enteros positivos).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Utilice números enteros positivos sólo cuando se crea un nuevo `Array` objeto. Si desea crear una matriz con un solo elemento que no es un entero, puede hacerlo en un proceso en dos pasos. En primer lugar crear una matriz con un elemento, a continuación, coloque el valor del primer elemento (array[0]). El siguiente es un ejemplo que genera este error.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     El ejemplo siguiente muestra la forma correcta para especificar una matriz con un solo elemento numérico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     No hay ningún límite superior para el tamaño de una matriz, que no sea el valor entero máximo (aproximadamente 4 mil millones).  
  
## <a name="see-also"></a>Vea también  
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)
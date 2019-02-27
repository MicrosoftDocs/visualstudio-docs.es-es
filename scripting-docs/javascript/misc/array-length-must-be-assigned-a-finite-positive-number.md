---
title: Longitud de la matriz debe asignarse un valor entero positivo finito | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c6e536047aaebb9bd3a06e38574330937817748
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840797"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Se debe asignar un valor entero positivo finito a la longitud de la matriz
Al establecer el **longitud** propiedad de un miembro de **matriz** objeto, se especifica una longitud de la matriz que no era un número positivo o cero. Este error se produce cuando se asigna un valor para el **longitud** propiedad de un `Array` objeto que es negativo o no es un número (`NaN`). Tenga en cuenta que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convierte automáticamente los números fraccionarios enteros.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asignar un número entero positivo a la propiedad length. No hay ningún límite superior para el tamaño de una matriz, que no sea el valor entero máximo (aproximadamente 4 mil millones). En el ejemplo siguiente se muestra la forma correcta para establecer el **longitud** propiedad de un **matriz** objeto.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)
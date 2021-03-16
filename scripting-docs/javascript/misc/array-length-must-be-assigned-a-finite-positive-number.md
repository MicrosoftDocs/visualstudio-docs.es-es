---
description: Al establecer la propiedad longitud de un objeto de matriz existente, se especificó una longitud de matriz que no era un número positivo o cero.
title: Se debe asignar un número positivo finito a la longitud de la matriz | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 3938f240580564112915ab0ba3036b63dc96cd8f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572148"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Se debe asignar un valor entero positivo finito a la longitud de la matriz
Al establecer la propiedad **longitud** de un objeto de **matriz** existente, se especificó una longitud de matriz que no era un número positivo o cero. Este error se produce cuando se asigna un valor a la propiedad **length** de un `Array` objeto que es negativo o no es un número ( `NaN` ). Tenga en cuenta que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convierte automáticamente los números fraccionarios en enteros completos.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asigne un número entero positivo a la propiedad longitud. No hay ningún límite superior para el tamaño de una matriz, excepto el valor entero máximo (aproximadamente 4 mil millones). En el ejemplo siguiente se muestra la manera correcta de establecer la propiedad **length** de un objeto **array** .  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Usar matrices](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)

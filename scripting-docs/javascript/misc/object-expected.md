---
description: Se intentó invocar un método o una propiedad en un objeto de un tipo que no es Object, o bien se pasó un argumento de un tipo que no sea Object cuando se requería un objeto.
title: Objeto esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a62a68b8dd5289794086dad6858238db6cc4f449
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572070"
---
# <a name="object-expected"></a>Se esperaba un objeto
Se intentó invocar un método o propiedad en un objeto de un tipo distinto de `Object`, o se pasó un argumento de un tipo distinto de `Object` cuando se requería `Object`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Invoque el método o propiedad solo en objetos de tipo `Object`.  
  
- Si se produce un error para un argumento que no es de objeto, pase un objeto de tipo `Object`.  
  
- Compruebe si se está invocando una referencia nula o indefinida en lugar de un objeto de tipo `Object`.  
  
     Por ejemplo, si obtiene este error en myVar en el código siguiente:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     puede usar en su lugar este código:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Objeto de objeto](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Objetos y matrices](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)

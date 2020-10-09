---
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
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862117"
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
  
## <a name="see-also"></a>Vea también  
 [Objeto de objeto](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Objetos y matrices](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)
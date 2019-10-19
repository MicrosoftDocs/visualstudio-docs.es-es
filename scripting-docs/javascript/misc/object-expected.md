---
title: Objeto esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 1611596d844d43ef72663154dc48791830dfe29f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573735"
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
 Objeto de [objeto](../../javascript/reference/object-object-javascript.md)    
 [Objetos y matrices](../../javascript/objects-and-arrays-javascript.md)
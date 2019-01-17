---
title: Se esperaba un objeto | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49d66c82081af06bf23a43922629a579a6d6f590
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345791"
---
# <a name="object-expected"></a>Se esperaba un objeto
Se intentó invocar un método o propiedad en un objeto de un tipo distinto de `Object`, o se pasó un argumento de un tipo distinto de `Object` cuando se requería `Object`.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Invoque el método o propiedad solo en objetos de tipo `Object`.  
  
-   Si se produce un error para un argumento que no es de objeto, pase un objeto de tipo `Object`.  
  
-   Compruebe si se está invocando una referencia nula o indefinida en lugar de un objeto de tipo `Object`.  
  
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
 [Object (objeto)](../../javascript/reference/object-object-javascript.md)   
 [Objetos y matrices](../../javascript/objects-and-arrays-javascript.md)
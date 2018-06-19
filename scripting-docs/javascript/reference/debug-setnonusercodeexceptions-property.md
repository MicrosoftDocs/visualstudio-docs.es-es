---
title: Debug.setNonUserCodeExceptions (propiedad) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636165"
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions (Propiedad)
Determina si los bloques try-catch en este ámbito se tratará el depurador como no controlada por el usuario. Excepciones se clasifica como produce, no controlada por el usuario o no controladas.  
  
 Si esta propiedad se establece en `true` en un ámbito determinado, el depurador puede determinar, a continuación, realizar alguna acción (por ejemplo, interrumpir) en las excepciones producidas dentro de ese ámbito si el desarrollador desea interrumpir en las excepciones no controladas por el usuario. Si esta propiedad se establece en `false` es el mismo que si nunca se ha establecido la propiedad.  
  
 Para obtener más información sobre la depuración, vea [Active Script información general sobre depuración](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo establecer esta propiedad.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
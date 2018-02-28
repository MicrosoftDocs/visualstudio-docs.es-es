---
title: Objeto de enumerador (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Enumerator (Objeto de JavaScript)
Permite la enumeración de elementos en una colección.  
  
> [!WARNING]
>  Este objeto solo es compatible con Internet Explorer, no con las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Parámetros  
 `enumObj`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Enumerator` .  
  
 `collection`  
 Opcional. Cualquier objeto de la colección.  
  
## <a name="remarks"></a>Comentarios  
 Las colecciones se diferencian de las matrices en que los miembros de una colección no son accesibles directamente. En lugar de usar índices, como lo haría con las matrices, puede mover el puntero del elemento actual solo al primer o al siguiente elemento de una colección.  
  
 El objeto `Enumerator` proporciona una manera de tener acceso a cualquier miembro de una colección y se comporta de forma similar a la instrucción `For...Each` en VBScript.  
  
## <a name="example"></a>Ejemplo  
 El siguiente código muestra el uso del objeto `Enumerator` :  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>Propiedades  
 El objeto `Enumerator` no tiene propiedades.  
  
## <a name="methods"></a>Métodos  
 [atEnd (método)](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [item (método)](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [moveFirst (método)](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext (método)](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Vea también  
 [Boolean (Objeto)](../../javascript/reference/boolean-object-javascript.md)
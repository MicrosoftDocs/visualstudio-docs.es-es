---
title: "moveFirst (método, Enumerator) (JavaScript) | Documentos de Microsoft"
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
- moveFirst
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveFirst method
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8c59194a5655730e8509b43533f699aeef51d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="movefirst-method-enumerator-javascript"></a>moveFirst (Método, Enumerator de JavaScript)
Restablece el elemento actual de la colección en el primer elemento.  
  
> [!WARNING]
>  Este objeto solo es compatible con Internet Explorer.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
enumObj.moveFirst( )   
```  
  
## <a name="remarks"></a>Comentarios  
 La referencia *enumObj* necesaria es cualquier objeto `Enumerator` .  
  
 Si no hay ningún elemento en la colección, el elemento actual se establece como no definido.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, el método `moveFirst` se usa para evaluar miembros de la colección `Drives` desde el principio de la lista:  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [atEnd (método, Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Item (método, Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveNext (Método, Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)
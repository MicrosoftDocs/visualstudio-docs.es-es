---
title: Item (método, Enumerator) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- item
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Item method
ms.assetid: a88e93f2-42df-4578-a4f9-0760bd074185
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94275b2c82f199c96ef2d6c7d667fd27fba2702d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637525"
---
# <a name="item-method-enumerator-javascript"></a>item (Método, Enumerator de JavaScript)
Devuelve el elemento actual de la colección.  
  
> [!WARNING]
>  Este objeto solo es compatible con Internet Explorer.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
enumObj.item()   
```  
  
## <a name="remarks"></a>Comentarios  
 La referencia *enumObj* necesaria es cualquier objeto `Enumerator` .  
  
 El método **item** devuelve el elemento actual. Si la colección está vacía o el elemento actual no está definido, devuelve **undefined**.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente código, el método **item** se usa para devolver un miembro de la colección `Drives` .  
  
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
 [moveFirst (método, Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext (Método, Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)
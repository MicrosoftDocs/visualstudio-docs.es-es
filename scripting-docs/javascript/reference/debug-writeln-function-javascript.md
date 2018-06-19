---
title: Debug.writeln (función) (JavaScript) | Documentos de Microsoft
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
- writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636285"
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln (Función de JavaScript)
Envía las cadenas al depurador de scripts, seguido por un carácter de nueva línea.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 *str1, str2,..., strN*  
 Opcional. Cadenas para enviar al depurador de scripts.  
  
## <a name="remarks"></a>Comentarios  
 El `Debug.writeln` función envía las cadenas, seguido de un carácter de nueva línea, en la ventana Inmediato de Microsoft Script Debugger en tiempo de ejecución. Si la secuencia de comandos no se está depurando, la `Debug.writeln` función no tiene ningún efecto.  
  
 El `Debug.writeln` función es casi idéntica a la `Debug.write` (función). La única diferencia es que el `Debug.write` función no envía un carácter de nueva línea después de enviar las cadenas.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza la `Debug.writeln` función para mostrar el valor de la variable en la ventana Inmediato del depurador de Script de Microsoft.  
  
> [!NOTE]
>  Para ejecutar este ejemplo, debe tener instalado un depurador de scripts y la secuencia de comandos debe ejecutar en modo de depuración.  
>   
>  Internet Explorer 8 incluye el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Si usa una versión anterior de Internet Explorer, consulte [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Debug (objeto)](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Debug.write (Función)](../../javascript/reference/debug-write-function-javascript.md)
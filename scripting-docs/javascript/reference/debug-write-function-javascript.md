---
title: Debug.Write (función) (JavaScript) | Documentos de Microsoft
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
- Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636305"
---
# <a name="debugwrite-function-javascript"></a>Debug.write (Función de JavaScript)
Envía las cadenas al depurador de scripts.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 *str1, str2,..., strN*  
 Opcional. Cadenas para enviar al depurador de scripts.  
  
## <a name="remarks"></a>Comentarios  
 El `Debug.write` función envía las cadenas en la ventana Inmediato de un depurador de script en tiempo de ejecución. Si la secuencia de comandos no se está depurando, la `Debug.write` función no tiene ningún efecto.  
  
 El `Debug.write` función es casi idéntica a la `Debug.writeln` (función). La única diferencia es que el `Debug.writeln` función envía un carácter de nueva línea después de que se envían las cadenas.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza la `Debug.write` función para mostrar el valor de la variable en la ventana Inmediato del depurador de script.  
  
> [!NOTE]
>  Para ejecutar este ejemplo, debe tener instalado un depurador de scripts y la secuencia de comandos debe ejecutar en modo de depuración.  
>   
>  Internet Explorer 8 incluye el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] depurador. Si usa una versión anterior de Internet Explorer, consulte [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Debug (objeto)](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Debug.writeln (Función)](../../javascript/reference/debug-writeln-function-javascript.md)
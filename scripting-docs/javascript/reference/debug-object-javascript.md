---
title: Debug (objeto) (JavaScript) | Documentos de Microsoft
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
- debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Debug (Objeto de JavaScript)
Un objeto global intrínseco que envía la salida a un depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>Comentarios  
 El usuario no crea instancias del objeto Debug. Puede acceder a todas sus propiedades y métodos mediante una llamada a `function`.  
  
 Hay diferentes maneras de depurar Internet Explorer y las aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . En las aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] , las funciones `write` y `writeln` del objeto `Debug` muestra las cadenas en la ventana **Salida** de Visual Studio en tiempo de ejecución. Para obtener más información sobre la depuración [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicaciones, consulte [aplicaciones universales de Windows depurar en Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md).  
  
 Para depurar scripts de Internet Explorer, debe tener instalado un depurador de scripts y el script debe ejecutarse en modo de depuración. Internet Explorer 8 y las versiones posteriores incluyen el depurador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Si usa una versión anterior de Internet Explorer, consulte [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Si el script no se está depurando, las funciones no surten efecto.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se usa la función `write` para mostrar el valor de la variable.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>Constantes  
 [Constantes de depuración](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>Propiedades  
 [Debug.debuggerEnabled (propiedad)](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions (propiedad)](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>Funciones  
 [Debug.msTraceAsyncCallbackStarting (función)](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Debug.msTraceAsyncCallbackCompleted (función)](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Debug.msTraceAsyncOperationCompleted (función)](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Debug.msTraceAsyncOperationStarting (función)](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Debug.msUpdateAsyncCallbackRelation (función)](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write (función)](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln (función)](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [debugger (Instrucción)](../../javascript/reference/debugger-statement-javascript.md)
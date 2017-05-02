---
title: "Debug (Objeto de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debug (objeto)"
  - "Debug (objeto), acerca del objeto Debug"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debug (Objeto de JavaScript)
Un objeto global intrínseco que envía la salida a un depurador.  
  
## Sintaxis  
  
```  
Debug.function  
```  
  
## Comentarios  
 El usuario no crea instancias del objeto Debug. Puede acceder a todas sus propiedades y métodos mediante una llamada a `function`.  
  
 Hay diferentes maneras de depurar Internet Explorer y las aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. En las aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], las funciones `write` y `writeln` del objeto `Debug` muestra las cadenas en la ventana **Salida** de Visual Studio en tiempo de ejecución. Para más información sobre la depuración de las aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], vea [Depurar aplicaciones en Visual Studio](~/debugger/debug-store-apps-in-visual-studio.md).  
  
 Para depurar scripts de Internet Explorer, debe tener instalado un depurador de scripts y el script debe ejecutarse en modo de depuración. Internet Explorer 8 y las versiones posteriores incluyen el depurador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Si usa una versión anterior de Internet Explorer, consulte [Cómo: Habilitar e iniciar la depuración de script desde Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Si el script no se está depurando, las funciones no surten efecto.  
  
## Ejemplo  
 Este ejemplo se usa la función `write` para mostrar el valor de la variable.  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Constantes  
 [Constantes DEBUG](../../javascript/reference/debug-constants.md)  
  
## Propiedades  
 [Debug.debuggerEnabled \(Propiedad\)](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions \(Propiedad\)](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## Funciones  
 [Debug.msTraceAsyncCallbackStarting \(Función\)](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Debug.msTraceAsyncCallbackCompleted \(Función\)](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Debug.msTraceAsyncOperationCompleted \(Función\)](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Debug.msTraceAsyncOperationStarting \(Función\)](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Debug.msUpdateAsyncCallbackRelation \(Función\)](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write \(Función\)](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln \(Función\)](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## Vea también  
 [debugger \(Instrucción\)](../../javascript/reference/debugger-statement-javascript.md)
---
title: "IDebugExpression (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression (interfaz)"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression (Interfaz)
Representa una expresión de forma asincrónica evaluada.  Los motores de scripts implementan normalmente esta interfaz.  Un depurador usa el IDE normalmente esta interfaz para habilitar una ventana o una ventana inspección inmediata de la ejecución.  
  
> [!NOTE]
>  La interfaz de `IDebugExpression` solo está disponible desde un marco de pila.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugExpression` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Inicia la evaluación de la expresión.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Anula la expresión.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina si se completa la operación.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Devuelve el resultado de la evaluación de la expresión como una cadena y el valor devuelto de la operación.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Devuelve el resultado de la evaluación de la expresión como una propiedad de depuración y el valor devuelto de la operación.|
---
title: "Constantes DEBUG_TEXT | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Constantes DEBUG_TEXT
Se utiliza durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## Sintaxis  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## Constantes  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en comparación con una instrucción.  Este marcador puede afectar a la manera en que el texto es analiza algunos lenguajes.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Si un valor devuelto está disponible, utilizará el llamador.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|No permita efectos secundarios.  Si se establece este marcador, la evaluación de expresiones no debe cambiar un estado en tiempo de ejecución.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Permitir puntos de interrupción durante la evaluación de texto.  Si este marcador no se establece, los puntos de interrupción omitirán durante la evaluación de texto.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Permitir los informes de error durante la evaluación de texto.  Si este marcador no se establece, los errores no se notifican al host durante la evaluación.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Indica que se va a evaluar la expresión a un contexto de código suficiente que ejecuta la expresión propia.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
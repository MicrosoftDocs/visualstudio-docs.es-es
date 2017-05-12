---
title: "IDebugApplication::FCanJitDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FCanJitDebug"
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FCanJitDebug
Determina si se registran en un depurador just\-in\-time de \(JIT\).  
  
## Sintaxis  
  
```  
BOOL FCanJitDebug();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 Si el método tiene éxito y registrar un depurador JIT, el método devuelve `TRUE`.  De lo contrario, devuelve `FALSE`.  
  
## Comentarios  
 Este método determina si se registran en un depurador JIT.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)
---
title: "IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FIsAutoJitDebugEnabled"
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FIsAutoJitDebugEnabled
Determina si un depurador just\-in\-time de \(JIT\) es host mudos registrados de la auto\- depuración.  
  
## Sintaxis  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 Si el método tiene éxito y un depurador JIT es host mudos registrados de la auto\- depuración, el método devuelve `TRUE`.  De lo contrario, devuelve `FALSE`.  
  
## Comentarios  
 Este método determina si un depurador JIT es host mudos registrados de la auto\- depuración.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)
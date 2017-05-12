---
title: "SCRIPT_DEBUGGER_OPTIONS (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS (Enumeración)"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS (Enumeraci&#243;n)
Indica un conjunto de opciones o de funciones que se aplican al depurador adjunto.  Utilizado en [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) y [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Estas constantes se implementan como PDM v10.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|SDO\_NONE|0x00000000|No se establece ninguna opción.|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|Indica que el runtime de script debe provocar eventos de BREAKREASON\_ERROR cuando se produce una excepción.  Esta opción se puede establecer el depurador, o el conjunto por código de usuario puede `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|Indica que el depurador adjunto admite los trabajadores web.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
---
title: "SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND (Enumeraci&#243;n)
Indica la clase de la excepción producida.  El método [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) utiliza esta enumeración.  
  
> [!IMPORTANT]
>  Estas constantes se implementan mediante PDM versión 11.0 y versiones posteriores.  Se encuentra en activdbg100.h.  
  
## Sintaxis  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## Miembros  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|ETK\_FIRST\_CHANCE|0x00000000|La excepción es una excepción de primera aparición.|  
|ETK\_USER\_UNHANDLED|0x00000001|La excepción no se controla en el código de usuario.|  
|ETK\_UNHANDLED|0x00000002|La excepción no se controla en el código.|  
  
## Vea también  
 [IActiveScriptErrorDebug110 \(Interfaz\)](../../winscript/reference/iactivescripterrordebug110-interface.md)
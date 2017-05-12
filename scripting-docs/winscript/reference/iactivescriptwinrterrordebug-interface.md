---
title: "IActiveScriptWinRTErrorDebug (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug (Interfaz)"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug (Interfaz)
Implementado por el motor de JavaScript para proporcionar información de error extendida de Windows en tiempo de ejecución de un evento de [BREAKREASON \(Enumeración\)](../../winscript/reference/breakreason-enumeration.md) .  Puede hacer un QueryInterface para obtenerlo de un objeto de [IActiveScriptError](../../winscript/reference/iactivescripterror.md) .  
  
> [!IMPORTANT]
>  Esta interfaz se implementa por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 La interfaz `IActiveScriptWinRTErrorDebug` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Devuelve la capacidad SID del error de Windows en tiempo de ejecución, si está disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Devuelve la cadena limitada Windows en tiempo de ejecución de la referencia de error, si está disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Devuelve la cadena limitada Windows en tiempo de ejecución del error, si está disponible.|
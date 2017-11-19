---
title: IActiveScriptWinRTErrorDebug (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34fcc4f1dc3ebc21f9303ba49f1709f2d023a29a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug (Interfaz)
Implementado por el motor de JavaScript para proporcionar la información ampliada de errores en tiempo de ejecución de Windows de un [enumeración BREAKREASON](../../winscript/reference/breakreason-enumeration.md) eventos. Puede realizar una operación de QueryInterface para obtenerlo de un [IActiveScriptError](../../winscript/reference/iactivescripterror.md) objeto.  
  
> [!IMPORTANT]
>  Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IActiveScriptWinRTErrorDebug` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Devuelve el SID de capacidad para el error en tiempo de ejecución de Windows, si está disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Devuelve el tiempo de ejecución de Windows restringe la cadena de referencia de error, si está disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Devuelve el tiempo de ejecución de Windows restringe la cadena de error, si está disponible.|
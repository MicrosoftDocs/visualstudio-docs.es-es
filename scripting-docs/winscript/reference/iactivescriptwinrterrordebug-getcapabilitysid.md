---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d53b498ba88fae50cfaca106a65a2bb07d21a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Devuelve el SID de capacidad para el error en tiempo de ejecución de Windows, si está disponible.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug (interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `capabilitySid`  
 La capacidad de SID del error.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptWinRTErrorDebug (Interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)
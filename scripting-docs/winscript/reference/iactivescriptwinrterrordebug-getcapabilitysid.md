---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6847dba8f2bd3051df4ab6f0940e7b405698e45b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432953"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Devuelve la capacidad de SID para el error en tiempo de ejecución de Windows, si está disponible.  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug (interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `capabilitySid`  
 La funcionalidad de SID del error.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptWinRTErrorDebug (Interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)
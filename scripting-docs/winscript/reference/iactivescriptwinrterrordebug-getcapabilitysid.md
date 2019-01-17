---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2e0e9f642e780b745f8b66734893345618a43460
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349833"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Devuelve la capacidad de SID para el error en tiempo de ejecución de Windows, si está disponible.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug (interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `capabilitySid`  
 La funcionalidad de SID del error.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptWinRTErrorDebug (Interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)
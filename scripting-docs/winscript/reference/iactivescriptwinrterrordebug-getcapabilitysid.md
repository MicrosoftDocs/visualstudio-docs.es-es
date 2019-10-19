---
title: 'Iactivescriptwinrterrordebug (:: GetCapabilitySid | Microsoft Docs'
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
ms.openlocfilehash: 93bf824dd4d290ca536cb609e24b5d14400a3e3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577932"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Devuelve el SID de capacidad para el error de Windows Runtime, si está disponible.  
  
> [!IMPORTANT]
> La [interfaz iactivescriptwinrterrordebug (](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `capabilitySid`  
 SID de capacidad del error.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptWinRTErrorDebug (Interfaz)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)
---
title: 'Idebugapplicationnode100 (:: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574735"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Establece el filtro en una determinada implementación de la [interfaz idebugapplicationnodeevents (](../../winscript/reference/idebugapplicationnodeevents-interface.md) . Permite que los depuradores de script filtren los nodos de aplicación secundarios generados por el compilador para que el PDM deje de enviar eventos cuando se crean o se quitan. De forma predeterminada, se enviarán todos los nodos.  
  
> [!IMPORTANT]
> La [interfaz idebugapplicationnode100 (](../../winscript/reference/idebugapplicationnode100-interface.md) se implementa mediante PDM v 10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 Cookie del filtro.  
  
 `filter`  
 El filtro.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode100 (Interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md)
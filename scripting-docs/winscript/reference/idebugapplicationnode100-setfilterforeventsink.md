---
title: IDebugApplicationNode100::SetFilterForEventSink | Documentos de Microsoft
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
ms.openlocfilehash: f1a59f57daad90e5a7df1a8d8fa8d1ecd8c5c3bf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154301"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Establece el filtro en un determinado [IDebugApplicationNodeEvents (interfaz)](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementación. Permite a los depuradores de scripts filtrar los nodos de aplicación secundarios generados por el compilador para que el PDM no volverá a enviar eventos cuando estos se crean o se quitan. De forma predeterminada, se enviarán todos los nodos.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 (interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md) es implementada por PDM v10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 La cookie del filtro.  
  
 `filter`  
 El filtro.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode100 (Interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md)
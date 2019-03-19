---
title: Método Iactivescripttraceinfo | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 824d60ef0f17012524f9d0150a90ccd9efcfb3a9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150964"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing (Método)
Inicia el seguimiento de la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSiteTraceInfo`  
 Un puntero a IActiveScriptSiteTraceInfo del host.  
  
 `guidContextId`  
 El GUID del contexto.  
  
## <a name="return-value"></a>Valor devuelto  
 Los valores devueltos posibles para este método son los siguientes:  
  
1.  S_OK: Correcto.  
  
2.  E_POINTER: `pSiteTraceInfo` es un puntero NULL.  
  
3.  E_NOTIMPL: Sin implementar.
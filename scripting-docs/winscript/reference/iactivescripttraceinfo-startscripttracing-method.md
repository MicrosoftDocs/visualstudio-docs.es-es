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
ms.openlocfilehash: b87971e1fd2e484aa54ff4de56ee56e00b19b1e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991198"
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
  
1. S_OK: Correcto.  
  
2. E_POINTER: `pSiteTraceInfo` es un puntero NULL.  
  
3. E_NOTIMPL: Sin implementar.
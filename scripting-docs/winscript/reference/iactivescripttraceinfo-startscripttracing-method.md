---
title: Método Iactivescripttraceinfo | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6462597f55b6b0ceee885d207572e9669a350600
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093649"
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
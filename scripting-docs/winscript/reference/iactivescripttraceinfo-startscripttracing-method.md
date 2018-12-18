---
title: 'Iactivescripttraceinfo:: Startscripttracing (método) | Documentos de Microsoft'
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
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724885"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing (Método)
Inicia el seguimiento de la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSiteTraceInfo`  
 Un puntero a IActiveScriptSiteTraceInfo del host.  
  
 `guidContextId`  
 El GUID del contexto.  
  
## <a name="return-value"></a>Valor devuelto  
 Los posibles valores devueltos para este método son los siguientes:  
  
1.  S_OK: correcto.  
  
2.  E_POINTER: `pSiteTraceInfo` es un puntero NULL.  
  
3.  E_NOTIMPL: No implementado.
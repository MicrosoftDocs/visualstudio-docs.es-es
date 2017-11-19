---
title: "Iactivescriptsitetraceinfo:: Sendscripttraceinfo (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5290cc6a92be7c8bc99e4715c77bfe6f8f6abb53
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitetraceinfosendscripttraceinfo-method"></a>IActiveScriptSiteTraceInfo::SendScriptTraceInfo (Método)
Envía información de seguimiento que incluye el tipo de evento, el contexto y la instrucción de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SendScriptTraceInfo(     [in] SCRIPTTRACEINFO stiEventType,     [in] GUID guidContextID,     [in] DWORD dwScriptContextCookie,     [in] LONG lScriptStatementStart,     [in] LONG lScriptStatementEnd,     [in] DWORD64 dwReserved );   
```  
  
#### <a name="parameters"></a>Parámetros  
 `stiEventType`  
 El tipo de evento.  
  
 `guidContextId`  
 El GUID del contexto.  
  
 `dwScriptContextCookie`  
 La cookie del contexto.  
  
 `lScriptStatementStart`  
 La ubicación de inicio de la instrucción de script.  
  
 `lScriptStatementEnd`  
 La ubicación del final de la instrucción de script.  
  
 `dwReserved`  
 Reservado.
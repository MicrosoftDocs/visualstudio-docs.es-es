---
title: IActiveScriptError::GetExceptionInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8719d1a169c89d7b6cf712a125b6962b9c7a8839
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645725"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Recupera información sobre un error que se produjeron mientras el motor de scripting estaba ejecutando una secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pexcepinfo`  
 [out] Dirección de un `EXCEPINFO` estructura que recibe información de error.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_FAIL` si se produjo un error.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)
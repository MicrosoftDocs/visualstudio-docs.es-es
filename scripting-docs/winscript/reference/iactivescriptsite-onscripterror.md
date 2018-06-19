---
title: IActiveScriptSite::OnScriptError | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724635"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informa al host que se produjo un error de ejecución mientras el motor estaba ejecutando la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pase`  
 [in] Dirección del objeto error [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interfaz. Un host puede utilizar esta interfaz para obtener información sobre el error de ejecución.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si el error se administra correctamente, o un definido por OLE código de error en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)
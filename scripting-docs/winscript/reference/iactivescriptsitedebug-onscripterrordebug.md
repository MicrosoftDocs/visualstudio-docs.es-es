---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5680d22ffa5ec648afaced5e98f651e35758f929
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092123"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Permite a un host inteligente determinar cómo controlar los errores de tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pErrorDebug`  
 [in] El error de tiempo de ejecución  
  
 `pfEnterDebugger`  
 [out] Marca que indica si se debe pasar el error al depurador para realizar la depuración de JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Marca que indica si se debe llamar a `IActiveScriptSite::OnScriptError` cuando el usuario decide continuar sin depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Los valores posibles incluyen, pero no se limita al valor en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente puede usar este método para determinar cómo controlar los errores de tiempo de ejecución.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug (Interfaz)](../../winscript/reference/iactivescriptsitedebug-interface.md)
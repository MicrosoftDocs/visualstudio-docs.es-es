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
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088418"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informa al host que se ha producido un error de ejecución mientras el motor estaba ejecutando la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pase`  
 [in] Dirección del objeto error [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interfaz. Un host puede utilizar esta interfaz para obtener información sobre el error de ejecución.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si el error se controló correctamente o OLE definido por el código de error en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)
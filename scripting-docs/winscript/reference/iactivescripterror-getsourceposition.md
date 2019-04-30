---
title: IActiveScriptError::GetSourcePosition | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009629"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Recupera la ubicación en el código fuente donde se produjo un error mientras el motor de scripting estaba ejecutando una secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwSourceContext`  
 [out] Dirección de una variable que recibe una cookie que identifica el contexto. La interpretación de este parámetro depende de la aplicación host.  
  
 `pulLineNumber`  
 [out] Dirección de una variable que recibe el número de línea en el archivo de origen donde se produjo el error.  
  
 `pichCharPosition`  
 [out] Dirección de una variable que recibe la posición del carácter en la línea donde se produjo el error.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_FAIL` si no se ha recuperado la ubicación.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)
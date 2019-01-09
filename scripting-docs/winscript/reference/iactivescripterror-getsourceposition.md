---
title: IActiveScriptError::GetSourcePosition | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fb5adfe508b7b5d3de0cf7f508d8c801a36adf1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097375"
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
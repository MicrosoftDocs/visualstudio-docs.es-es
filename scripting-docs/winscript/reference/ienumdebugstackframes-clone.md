---
title: IEnumDebugStackFrames::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 978a96fdb08c460ead1b09bdc20ef6a8cf886c57
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093813"
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
Crea un enumerador que contiene el mismo estado que el enumerador actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppedsf`  
 [out] Devuelve el `IEnumDebugStackFrames` interfaz del clon del enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método crea un enumerador que contiene el mismo estado que el enumerador actual.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugStackFrames (Interfaz)](../../winscript/reference/ienumdebugstackframes-interface.md)
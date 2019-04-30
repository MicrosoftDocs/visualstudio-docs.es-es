---
title: IEnumDebugStackFrames::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 117ed9923936a7211c1cc871fa084c269bd2a270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963382"
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
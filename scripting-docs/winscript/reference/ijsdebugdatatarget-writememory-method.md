---
title: 'IJsDebugDataTarget:: Writememory ((método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572421"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory (Método)
Lee la memoria del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 de Dirección base desde la que se va a escribir la memoria del proceso de destino.  
  
 `pMemory`  
 de Los datos que se van a escribir en el espacio de direcciones del proceso especificado.  
  
 `size`  
 de Número de bytes que se van a escribir en el proceso.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Antes de que se produzca la transferencia de datos, el sistema comprueba que todos los datos de la dirección base y la memoria del tamaño especificado son accesibles para el acceso de escritura y, si no es accesible, la función genera un error E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)
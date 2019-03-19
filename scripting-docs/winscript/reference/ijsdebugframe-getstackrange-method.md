---
title: Método Ijsdebugframe | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52dd6114d3ec462f91f8bce5e76f73c5487746ed
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147441"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange (Método)
Devuelve el intervalo de direcciones absolutas del marco de pila de JavaScript lógico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStart`  
 [out] Bottom mayoría puntero de pila del marco.  
  
 `pEnd`  
 [out] Principales puntero de apilador del marco.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Este método es útil para juntar los seguimientos de pila intercalados recopilados de varios entornos de ejecución. El inicio, los punteros de pila final pueden abarcar varios marcos de pila de máquina física (para marcos de tiempo de ejecución JavaScript interpretados). Inicio > termine conforme la pila crece desde alto a bajo dirección.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)
---
title: IEnumDebugFrameInfo2::GetCount | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::GetCount
helpviewer_keywords:
- IEnumDebugFrameInfo2::GetCount
ms.assetid: d02a08e3-f34f-461e-8195-5157e154c481
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 421fa9a2b6f1cb78893902f5692d9ee9348f677d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161054"
---
# <a name="ienumdebugframeinfo2getcount"></a>IEnumDebugFrameInfo2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve el número de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcelt`  
 [out] Devuelve el número de elementos de la enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método no forma parte de la interfaz de enumeración COM habitual que especifica que solamente el `Next`, `Clone`, `Skip`, y `Reset` métodos deben implementarse.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

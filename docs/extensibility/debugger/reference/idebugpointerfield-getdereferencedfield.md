---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 685499cae556a50a5e98e8fe32e8104098cc79e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933253"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Este método devuelve el tipo de objeto al que señala este objeto de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppField`  
 [out] Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el tipo de objeto de destino.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, si la [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) objeto apunta a un entero, el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ese tipo entero describe el tipo devuelto por este método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
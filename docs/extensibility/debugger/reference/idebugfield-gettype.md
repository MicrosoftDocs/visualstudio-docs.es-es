---
title: IDebugField::GetType | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad684837fcda28fbe45874e5a5573f4581a9217f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
Este método obtiene el tipo de campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppType`  
 [out] Devuelve el tipo de campo porque hay otra [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
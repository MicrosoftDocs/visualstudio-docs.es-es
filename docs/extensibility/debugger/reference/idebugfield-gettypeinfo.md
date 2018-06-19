---
title: IDebugField::GetTypeInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3354a67d5d92aeebf67216ed22ed46666d4fc5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111100"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Este método obtiene independiente del tipo de información sobre el tipo o el símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pTypeInfo`  
 [out] Devuelve información de tipo en proporcionado [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructura.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Independiente del tipo de información incluyen, por ejemplo, el dominio de aplicación, el módulo y la clase que contiene el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
---
title: IDebugField::GetContainer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 826274b42aad8e695772abab75d4a2d5f2611336
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Este método obtiene el contenedor de un campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppContainerField`  
 [out] Devuelve el contenedor tal como está representado por la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si este campo no tiene un contenedor, el valor devuelto `ppContainerField` será un valor null.  
  
## <a name="see-also"></a>Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
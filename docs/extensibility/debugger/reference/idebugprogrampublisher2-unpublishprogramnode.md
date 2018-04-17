---
title: IDebugProgramPublisher2::UnpublishProgramNode | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d62c68bfc8e43370105a94818437bb0cfa2221e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
Quita un nodo de programa de disponibilidad para depurar los motores (DEs) y el Administrador de sesión de depuración (SDM).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT UnpublishProgramNode(  
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int UnpublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProgramNode`  
 [in] Un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa el nodo de programa que se va a quitar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una vez quitado, el nodo de programa ya no está disponible para consultar la información del programa.  
  
 Para disponer de un nodo de programa, llame a la [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
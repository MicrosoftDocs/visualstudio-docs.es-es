---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e82f2d1635b46dccd9f5f93b5773ba757342f04d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839003"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el objeto al que señala.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwIndex`  
 [in] Desplazamiento de bytes simple desde el principio del objeto que apunta.  
  
 `ppObject`  
 [out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de objeto que representa el objeto señalado, además de desplazamiento, si existe.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error. Devuelve E_FAIL si este objeto no apunta a otro objeto.  
  
## <a name="remarks"></a>Comentarios  
 Puede ser el objeto al que señala a un tipo primitivo o un tipo más complejo como una clase o estructura.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)


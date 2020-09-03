---
title: IDebugPointerObject::D ereference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40a0e66e5f3cb3a50618a3c8dd4fd5926c34c624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200998"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el objeto al que se apunta.  
  
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
 de Desplazamiento de bytes simple desde el principio del objeto al que se apunta.  
  
 `ppObject`  
 enuncia Devuelve un objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto al que se apunta, más el desplazamiento, si existe.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error. Devuelve E_FAIL si este objeto no apunta a otro objeto.  
  
## <a name="remarks"></a>Comentarios  
 El objeto al que se señala puede ser un tipo primitivo o más complejo, como una clase o estructura.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)

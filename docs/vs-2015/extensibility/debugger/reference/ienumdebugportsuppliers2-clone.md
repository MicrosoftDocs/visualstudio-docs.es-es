---
title: IEnumDebugPortSuppliers2::Clone | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Clone
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Clone
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8f3fffab8f8adbb3a44da0ec313887498ef0e21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155001"
---
# <a name="ienumdebugportsuppliers2clone"></a>IEnumDebugPortSuppliers2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve una copia de la enumeración actual como un objeto independiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve una copia de esta enumeración como un objeto independiente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y el original son independientes y se pueden cambiar de forma individual.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)

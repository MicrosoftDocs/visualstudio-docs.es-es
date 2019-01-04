---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18d728f762a9e4dd16930e4634c9cb0ca47b2bc8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853910"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Comprueba que un proveedor de puerto puede agregar nuevos puertos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve si se puede agregar el puerto, `S_OK`; en caso contrario, devuelve `S_FALSE` para indicar que no hay puertos se pueden agregar a este proveedor del puerto.  
  
## <a name="remarks"></a>Comentarios  
 Llame a este método antes de llamar a la [agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) método, ya que el último método crea el puerto, así como agregarlo, que podría ser una operación lenta.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
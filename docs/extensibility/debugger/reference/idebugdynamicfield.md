---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8344417bdcb38ec29e183925cedc4da2338ab7a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882434"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Esta interfaz representa un tipo de una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante proveedores de símbolos como una clase base para cualquier tipo que se puede determinar en tiempo de ejecución. Esto es solo para código administrado.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz representa una clase base desde la que se pueden derivar las interfaces más especializadas.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz no proporciona ningún método distinto de los heredados de `IDebugField`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
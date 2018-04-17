---
title: IDebugPortSupplierLocale2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1cd0160b1ec5b1c9d86c277f2b47011d1b7610c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Proporciona compatibilidad de configuración regional para un proveedor del puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz para establecer la configuración regional.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de **IDebugPortSupplierLocale2**.  
  
|Método|Descripción|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Establece la configuración regional para el proveedor del puerto.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
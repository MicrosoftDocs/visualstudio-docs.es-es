---
title: IDebugPortPicker | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d9a5a830d6b3b0d191b5eae84bf625ffdb3b695
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa una interfaz de usuario personalizada para seleccionar el puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante proveedores de puertos. Un proveedor de puerto define su selector de puerto para exponer como CLSID y elige el `metricPortPickerCLSID` métrica en el CLSID expuesto.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugPortPicker`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Establece el proveedor de servicios.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
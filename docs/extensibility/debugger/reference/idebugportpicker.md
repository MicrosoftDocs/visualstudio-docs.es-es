---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5546895231415cdf8092dcadd1dce7a65e72707a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914256"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa una interfaz de usuario personalizada para seleccionar el puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante proveedores de puertos. Un proveedor de puerto define su selector de puerto para exponerlo como un CLSID y elige el `metricPortPickerCLSID` métrica en el CLSID expuesto.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugPortPicker`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Establece el proveedor de servicios.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
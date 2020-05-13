---
title: IDebugPortPicker ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724836"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa una interfaz de usuario personalizada para seleccionar el puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz es implementada por los proveedores de puertos. Un proveedor de puertos define su selector de puertos exponiéndolo como un CLSID y apuntando la `metricPortPickerCLSID` métrica al CLSID expuesto.

## <a name="methods"></a>Métodos
 En la tabla siguiente `IDebugPortPicker`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Establece el proveedor de servicios.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

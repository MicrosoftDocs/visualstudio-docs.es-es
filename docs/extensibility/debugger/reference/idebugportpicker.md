---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 991480886c2c43c330ce37561d383ffdc420e214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340364"
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

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
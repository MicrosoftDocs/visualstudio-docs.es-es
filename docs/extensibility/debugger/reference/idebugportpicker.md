---
description: Representa una interfaz de usuario personalizada para seleccionar el puerto.
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 335a954603505d064f32e8f901ce428d6cb8dfa1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142641"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa una interfaz de usuario personalizada para seleccionar el puerto.

## <a name="syntax"></a>Syntax

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementan los proveedores de puertos. Un proveedor de puertos define su selector de puerto al exponerlo como un CLSID y apuntar `metricPortPickerCLSID` a la métrica en el CLSID expuesto.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugPortPicker` .

|Método|Descripción|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Establece el proveedor de servicios.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6199c959a7186a1c10d6efdc30bb0763941c347a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926118"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Esta interfaz representa un proceso en ejecución y sus programas. Esta interfaz existe como sustituto de varios métodos de la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Proporciona control sobre todos los programas del proceso.

> [!NOTE]
> Los métodos [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)y [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) están desusados y ya no deben usarse. Use en su lugar los métodos correspondientes en la `IDebugProcess3` interfaz.

## <a name="syntax"></a>Sintaxis

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementa un proveedor de Puerto personalizado para administrar programas como un grupo. Cuando los programas se administran como un grupo, puede controlar su ejecución y establecer un idioma para un evaluador de expresiones. Esta interfaz debe ser implementada por el proveedor del puerto.

## <a name="notes-for-callers"></a>Notas para llamadores
 El administrador de depuración de sesión (SDM) llama principalmente a esta interfaz para interactuar con un grupo de programas identificados en este proceso.

 Llame a [QueryInterface](/cpp/atl/queryinterface) en una interfaz [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa los siguientes métodos.

|Método|Descripción|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continúa la ejecución o paso a través de un proceso.|
|[Ejecutar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Comienza la ejecución de un proceso.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Los pasos reenvían una instrucción o instrucción en el proceso.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtiene la razón por la que se inició el proceso para la depuración.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Establece el lenguaje de hospedaje para que el motor de depuración pueda cargar el evaluador de expresiones adecuado.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera el idioma establecido actualmente para este proceso.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deshabilita editar y continuar (ENC) para este proceso.<br /><br /> Un proveedor de Puerto personalizado no implementa este método (siempre debe devolver `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obtiene el estado de ENC para este proceso.<br /><br /> Un proveedor de Puerto personalizado no implementa este método (siempre debe devolver `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matriz de identificadores únicos para los motores de depuración disponibles.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

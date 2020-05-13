---
title: IDebugProcess3 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723545"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Esta interfaz representa un proceso en ejecución y sus programas. Esta interfaz existe como un reemplazo de varios métodos en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz. Proporciona control sobre todos los programas en el proceso.

> [!NOTE]
> [Los](../../../extensibility/debugger/reference/idebugprogram2-continue.md)métodos Continue , [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)y [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) están en desuso y ya no se deben usar. Utilice los métodos `IDebugProcess3` correspondientes en la interfaz en su lugar.

## <a name="syntax"></a>Sintaxis

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz es implementada por un proveedor de puertos personalizado para administrar programas como un grupo. Cuando los programas se administran como un grupo, puede controlar su ejecución y establecer un lenguaje para un evaluador de expresiones. Esta interfaz debe ser implementada por el proveedor del puerto.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz es llamada principalmente por el administrador del debug de la sesión (SDM) para interactuar con un grupo de programas identificados en este proceso.

 Llame a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continúa la ejecución o el paso a paso de un proceso.|
|[Ejecutar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Comienza la ejecución de un proceso.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Pasos hacia adelante una instrucción o instrucción en el proceso.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtiene la razón por la que se inició el proceso para la depuración.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Establece el lenguaje de hospedaje para que el motor de depuración pueda cargar el evaluador de expresiones adecuado.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera el idioma establecido actualmente para este proceso.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deshabilita Editar y continuar (ENC) para este proceso.<br /><br /> Un proveedor de puerto personalizado no implementa `E_NOTIMPL`este método (siempre debe devolver ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obtenga el estado ENC para este proceso.<br /><br /> Un proveedor de puerto personalizado no implementa `E_NOTIMPL`este método (siempre debe devolver ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matriz de identificadores únicos para los motores de depuración disponibles.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

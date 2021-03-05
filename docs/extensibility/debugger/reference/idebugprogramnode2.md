---
description: Esta interfaz representa un programa que se puede depurar.
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d697ce389a7672f4f97efc17547e79173da3e2dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151576"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Esta interfaz representa un programa que se puede depurar.

## <a name="syntax"></a>Syntax

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor DE depuración (DE) o un proveedor de Puerto personalizado implementa esta interfaz para representar un programa que se puede depurar. Esta interfaz se implementa normalmente en el mismo objeto que implementa la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Esta interfaz se registra con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] llamando a [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) para devolver esta interfaz. Un proveedor de Puerto personalizado recibe esta interfaz a través de una llamada a [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Un DE recibe esta interfaz a través de una llamada a [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProgramNode2` .

|Método|Descripción|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Obtiene el nombre de un programa.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Obtiene el nombre del proceso que hospeda un programa.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Obtiene el identificador de proceso del sistema para el proceso que hospeda un programa.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|En desuso. NO USE.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|En desuso. NO USE. Vea la interfaz [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) para obtener un enfoque alternativo.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Obtiene el nombre y el identificador de la ejecución de este programa.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|En desuso. NO USE.|

## <a name="remarks"></a>Observaciones
 El administrador de depuración de sesión (SDM) normalmente llama a [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) para obtener esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

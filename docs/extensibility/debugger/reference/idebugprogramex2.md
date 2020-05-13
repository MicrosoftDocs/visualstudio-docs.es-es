---
title: IDebugProgramEx2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722333"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Esta interfaz permite que el administrador de depuración de sesión (SDM) se asocie a un programa y obtenga el nodo de programa asociado a un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que la [interfaz IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) con el fin de permitir que el SDM se asocie a un programa mientras que al mismo tiempo permite al proveedor de puertos realizar un seguimiento de todas las sesiones adjuntas al programa. El proveedor de puertos personalizado puede implementar esta interfaz si así lo desea.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El SDM llama a `IDebugProgram2` [QueryInterface](/cpp/atl/queryinterface) en una interfaz para obtener esta interfaz para realizar un seguimiento de las sesiones que se han asociado a los programas.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugProgramEx2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Asocia un programa a una sesión.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtiene el nodo de programa asociado a un programa.|

## <a name="remarks"></a>Observaciones
 Esta interfaz es privada entre el SDM y el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

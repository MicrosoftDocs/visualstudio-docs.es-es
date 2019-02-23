---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4339be57479b54d9d3f040670e9ce161f7cd4715
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683186"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Esta interfaz representa una posición en un archivo de origen abstracta.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio normalmente implementa esta interfaz. Un motor de depuración (DE) también podría implementar esta interfaz si debe proporcionar su propio código fuente (como cuando se implementa la DE la [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz).

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz se pasa como argumento a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). También se especifica como parte de un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (específicamente, un [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) estructura) que a su vez forma parte de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estructura, que se utiliza para crear un punto de interrupción pendiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugDocumentPosition2`.

|Método|Descripción|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtiene el nombre de archivo del archivo de origen que contiene la posición de este documento.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtiene el documento contenedor.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina si esta posición se encuentra en el documento especificado.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtiene el intervalo de esta posición del documento.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
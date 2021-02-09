---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7dc8537fc943e84e37d47dc02cf6264b16dd7fb3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874314"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Esta interfaz representa una posición abstracta en un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Normalmente, Visual Studio implementa esta interfaz. Un motor DE depuración (DE) también implementaría esta interfaz si debe proporcionar su propio código fuente (como cuando el DE implementa la interfaz [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) ).

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz se pasa como argumento a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). También se proporciona como parte de una Unión [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (concretamente, una estructura [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) ) que, a su vez, forma parte de la estructura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , que se usa para crear un punto de interrupción pendiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugDocumentPosition2` .

|Método|Descripción|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtiene el nombre de archivo del archivo de código fuente que contiene esta posición del documento.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtiene el documento que lo contiene.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina si esta posición está incluida en el documento especificado.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtiene el intervalo para esta posición del documento.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)

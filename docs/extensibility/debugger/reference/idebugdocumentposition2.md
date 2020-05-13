---
title: IDebugDocumentPosition2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731639"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Esta interfaz representa una posición abstracta en un archivo de origen.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio normalmente implementa esta interfaz. Un motor de depuración (DE) también implementaría esta interfaz si debe proporcionar su propio código fuente (como cuando el DE implementa el [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz se pasa como argumento a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). También se suministra como parte de una unión [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (específicamente, una estructura [de BP_LOCATION_CODE_FILE_LINE)](../../../extensibility/debugger/reference/bp-location-code-file-line.md) que a su vez forma parte de la estructura [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) que se utiliza para crear un punto de interrupción pendiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugDocumentPosition2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtiene el nombre de archivo del archivo de origen que contiene esta posición del documento.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtiene el documento contenedor.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina si esta posición está contenida en el documento especificado.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtiene el intervalo para esta posición de documento.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)

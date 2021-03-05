---
description: Esta interfaz representa un documento de texto.
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1c5928362616466985a6f88102ffcbf4377444
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154215"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Esta interfaz representa un documento de texto.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor DE depuración (DE) implementa esta interfaz cuando el código fuente que necesita proporcionar está en forma de texto. Dado que este es el caso más típico, si un DE implementa la interfaz [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , también debe implementar la `IDebugDocumentText2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use el `QueryInterface` método para obtener esta interfaz de una `IDebugDocument2` interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la `IDebugDocument2` interfaz, esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetSize (](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera el tamaño del texto en esta posición del documento.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera el texto de la posición especificada en el documento.|

## <a name="remarks"></a>Observaciones
 Un objeto que implementa esta interfaz también debe implementar la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz, que proporciona la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz para un objeto [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

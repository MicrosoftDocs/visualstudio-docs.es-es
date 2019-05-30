---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43716ce3b01464d2937fd75ce90ec5028679ef47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330645"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Esta interfaz representa un documento de texto.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor de depuración (DE) implementa esta interfaz cuando es el código fuente que debe proporcionar en forma de texto. Puesto que es el caso más habitual, si implementa a DE la [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz, también debe implementar la `IDebugDocumentText2` interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Use la `QueryInterface` método para obtener esta interfaz desde un `IDebugDocument2` interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos en el `IDebugDocument2` interfaz, esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera el tamaño del texto en esta posición en el documento.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera el texto de la posición especificada en el documento.|

## <a name="remarks"></a>Comentarios
 Un objeto que implementa esta interfaz debe implementar también la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz, que proporciona el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz para un [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objeto.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
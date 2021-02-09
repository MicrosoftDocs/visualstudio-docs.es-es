---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e611f6a4daf878042640697dca862015285078d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884876"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Esta interfaz representa un documento de origen.

## <a name="syntax"></a>Sintaxis

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] normalmente implementa esta interfaz. Un motor DE depuración (DE) también puede implementar esta interfaz cuando necesita proporcionar el código fuente y el origen no existe en el disco.  En tales casos, el DE también implementaría las interfaces [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) y [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) , así como algunos métodos adicionales en las interfaces [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) y [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 Los métodos de `IDebugDocumentContext2` las `IDebugDisassemblyStream2` interfaces,, `IDebugDocumentPosition2` y `IDebugActivateDocumentEvent2` devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugDocument2` .

|Método|Descripción|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtiene el nombre del documento en una de varias formas.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtiene el identificador de clase del documento.|

## <a name="remarks"></a>Notas
 Esta interfaz solo se implementa cuando el DE proporciona el código fuente. Por ejemplo, al depurar un script en una página HTML, el DE proporciona el código fuente porque el origen se descarga o se genera dinámicamente y no existe como archivo de disco. Al depurar lenguajes tradicionales, como C++, no es necesario implementar esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

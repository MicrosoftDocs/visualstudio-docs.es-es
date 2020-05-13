---
title: IDebugDocumentContext2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731730"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Esta interfaz representa una posición en un documento de archivo de origen.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con la depuración de nivel de código fuente. Además de una posición en el código fuente, esta interfaz proporciona métodos para comparar contextos y navegar por un documento de código fuente.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Los métodos de varias interfaces, normalmente las interfaces [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) y [GetDocumentContext,](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugDocumentContext2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Obtiene el documento que contiene este contexto de documento.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Obtiene el nombre que se puede mostrar del documento que contiene este contexto de documento.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Recupera una lista de todos los contextos de código asociados a este contexto de documento.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Obtiene el idioma asociado a este contexto de documento.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtiene el intervalo de instrucciones de archivo de este contexto de documento.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Obtiene el intervalo de origen de archivos de este contexto de documento.|
|[Comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Compara este contexto de documento con una matriz determinada de contextos de documento.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Mueve el contexto del documento por un número determinado de instrucciones o líneas.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)

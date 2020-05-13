---
title: IDebugActivateDocumentEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736620"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
El motor de depuración (DE) utiliza esta interfaz para solicitar que se cargue un documento.

## <a name="syntax"></a>Sintaxis

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz cuando necesita que se abra un archivo de origen. Esta interfaz solo se implementa mediante motores de depuración que funcionan con intérpretes de scripts o forman parte de ella. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta `IDebugEvent2` interfaz (el SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la interfaz).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 La DE crea y envía este objeto de evento cuando necesita tener un archivo de origen abierto. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugActivateDocumentEvent2`se muestran los métodos de .

|Métodos|Descripción|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Obtiene el documento que se va a activar.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la posición dentro del documento.|

## <a name="remarks"></a>Observaciones
 Un escenario típico en el que se utiliza esta interfaz es si se produce un error de análisis en el código de script en una página HTML, el script DE envía esta interfaz al SDM para que se pueda mostrar el documento con el error de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

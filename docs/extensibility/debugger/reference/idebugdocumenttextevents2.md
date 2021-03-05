---
description: Esta interfaz se utiliza para notificar a Visual Studio los cambios realizados en el documento de origen que proporciona el motor de depuración.
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bcbe6e44923172c3eac4da605848e972216837cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154189"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Esta interfaz se utiliza para notificar a Visual Studio los cambios realizados en el documento de origen que proporciona el motor de depuración.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para admitir la realización de cambios en el código fuente. Esta interfaz se implementa normalmente en el mismo objeto que implementa la interfaz [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] obtiene esta interfaz a través de una llamada al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz se obtiene de una llamada al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> método. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz se obtiene llamando al método [QueryInterface](/cpp/atl/queryinterface) en una interfaz [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugDocumentTextEvents2` .

|Método|Descripción|
|------------|-----------------|
|[Destruir](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que se ha destruido todo el documento.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al paquete de depuración que se ha insertado texto en el documento.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al paquete de depuración que se ha quitado el texto del documento.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al paquete de depuración que el texto se ha reemplazado en el documento.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al paquete de depuración que se han actualizado los atributos de texto en el documento.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al receptor el evento de que se han actualizado los atributos del documento.|

## <a name="remarks"></a>Observaciones
 Solo los motores de depuración que proporcionan sus propios documentos aprovecharán la `IDebugDocumentTextEvent2` interfaz. Un ejemplo de esto sería un motor de depuración de scripting. En el proceso de interpretar los scripts, se puede generar código fuente nuevo que no está presente en ningún archivo de disco y solo lo conoce el DE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

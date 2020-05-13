---
title: IDebugDocumentTextEvents2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731365"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Esta interfaz se usa para notificar a Visual Studio acerca de los cambios en el documento de origen proporcionados por el motor de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para admitir la realización de cambios en el código fuente. Esta interfaz se implementa normalmente en el mismo objeto que implementa el [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]obtiene esta interfaz a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> través de una llamada al método. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz se obtiene de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> una llamada al método. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz se obtiene mediante una llamada a la [QueryInterface](/cpp/atl/queryinterface) método en un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugDocumentTextEvents2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que se ha destruido todo el documento.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al paquete de depuración que el texto se ha insertado en el documento.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al paquete de depuración que el texto se ha quitado del documento.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al paquete de depuración que el texto se ha reemplazado en el documento.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al paquete de depuración que los atributos de texto se han actualizado en el documento.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al receptor del evento que se han actualizado los atributos del documento.|

## <a name="remarks"></a>Observaciones
 Solo los motores de depuración que suministran `IDebugDocumentTextEvent2` sus propios documentos aprovecharían la interfaz. Un ejemplo de esto sería un motor de depuración de secuencias de comandos. En el proceso de interpretación de scripts, se puede generar nuevo código fuente que no está presente en ningún archivo de disco y solo es conocido por la DE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

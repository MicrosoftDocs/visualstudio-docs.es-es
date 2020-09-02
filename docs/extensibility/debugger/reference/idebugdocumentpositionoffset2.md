---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731602"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Representa una posición en un archivo de código fuente como desplazamiento de caracteres.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Lo implementa el IDE y lo consumen los motores de depuración.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugDocumentPositionOffset2` .

|Método|Descripción|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera el intervalo para la posición del documento actual.|

## <a name="remarks"></a>Observaciones
 Esto devuelve la misma información que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , pero en `char` desplazamientos desde el principio del documento. Esto presenta el documento tal como lo haría en un disco, es decir, una matriz unidimensional de caracteres, en lugar de la información de línea y columna que se devuelve normalmente.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

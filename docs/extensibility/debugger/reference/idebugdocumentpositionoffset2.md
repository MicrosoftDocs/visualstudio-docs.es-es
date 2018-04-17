---
title: IDebugDocumentPositionOffset2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f08b278d75068351d6d65511f74209c7208024cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Representa una posición en un archivo de código fuente como un desplazamiento de caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementado por el IDE y utilizado por los motores de depuración.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugDocumentPositionOffset2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera el intervalo de la posición del documento actual.|  
  
## <a name="remarks"></a>Comentarios  
 Esto devuelve la misma información que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) pero en `char` desplazamientos desde el principio del documento. Esto presenta el documento como que existiría en un disco, es decir, una matriz unidimensional de caracteres, en lugar de la información de línea y columna que se devuelve normalmente.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
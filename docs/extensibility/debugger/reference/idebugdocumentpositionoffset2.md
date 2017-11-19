---
title: IDebugDocumentPositionOffset2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81c934add7248b7d63854b259957d58aae298401
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
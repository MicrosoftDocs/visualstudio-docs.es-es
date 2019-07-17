---
title: IDebugDocumentPositionOffset2 | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c1f30c3a465d4803e5c91f14ee45ad582e76d986
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200219"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa una posición en un archivo de código fuente como un desplazamiento de caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementado por el IDE y utilizado por los motores de depuración.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugDocumentPositionOffset2`.  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera el intervalo para la posición del documento actual.|  
  
## <a name="remarks"></a>Comentarios  
 Esto devuelve la misma información que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , pero en `char` desplazamientos desde el principio del documento. Esto presenta el documento como que existiría en un disco, es decir, una matriz unidimensional de caracteres, en lugar de la información de línea y columna que normalmente se devuelve.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

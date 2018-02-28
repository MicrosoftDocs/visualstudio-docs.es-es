---
title: IDebugAsyncOperation (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation (Interfaz)
El Administrador de procesos de depuración implementa el `IDebugAsyncOperation` interfaz. Llama a un motor de lenguaje el `IDebugApplication::CreateAsyncDebugOperation` método para obtener una referencia a esta interfaz. Puede usar el motor del lenguaje el `IDebugAsyncOperation` interfaz para proporcionar acceso asincrónico a una operación sincrónica de depuración.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugAsyncOperation` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Devuelve la operación sincrónica de depuración asociada a este objeto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Hace que la operación asincrónica empezar.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Cancela una operación.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina si se ha completado la operación de depuración.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Proporciona el valor devuelto y el parámetro de objeto de valor devuelto de la operación sincrónica de depuración.|
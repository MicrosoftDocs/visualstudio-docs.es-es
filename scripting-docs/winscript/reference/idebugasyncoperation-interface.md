---
title: IDebugAsyncOperation (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0088fddd2661d6711c9a18495f4b8704f782b3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350001"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation (Interfaz)
El Administrador de procesos de depuración implementa el `IDebugAsyncOperation` interfaz. Llama un motor de lenguaje el `IDebugApplication::CreateAsyncDebugOperation` método para obtener una referencia a esta interfaz. Puede usar el motor de lenguaje el `IDebugAsyncOperation` interfaz para proporcionar acceso asincrónico a una operación de depuración sincrónica.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugAsyncOperation` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Devuelve la operación de depuración sincrónica asociada a este objeto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Hace que la operación asincrónica empezar.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Cancela una operación.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina si se ha completado la operación de depuración.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Proporciona el valor devuelto y el parámetro de objeto de valor devuelto de la operación de depuración sincrónica.|
---
title: IDebugAsyncOperation (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821788"
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
---
title: IDebugSyncOperation (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724ad50771ca49460e130bf93ebc244681bd782
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349613"
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation (Interfaz)
Permite que un motor de scripts resumir una operación (por ejemplo, la evaluación de expresiones) que debe llevarse a cabo mientras esté anidada en un determinado subproceso bloqueado. La interfaz también proporciona un mecanismo para cancelar las operaciones que no responde.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugSyncOperation` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Devuelve el subproceso de la aplicación de destino para esta operación sincrónica.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Sincrónicamente realiza la operación y devuelve.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Cancela una operación en curso en otro subproceso.|
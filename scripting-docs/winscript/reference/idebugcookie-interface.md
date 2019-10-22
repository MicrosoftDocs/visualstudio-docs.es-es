---
title: Interfaz Idebugcookie (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573195"
---
# <a name="idebugcookie-interface"></a>IDebugCookie (Interfaz)
Permite establecer la cookie de depuración, para su uso con la interfaz `IMachineDebugManagerCookie`. Para obtener más información, vea [imachinedebugmanagercookie ((interfaz](../../winscript/reference/imachinedebugmanagercookie-interface.md)). El administrador de depuración de proceso (PDM) implementa esta interfaz y la utilizan los depuradores de scripts.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, la interfaz de `IDebugCookie` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Establece la cookie de la aplicación de depuración.|  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManagerCookie (Interfaz)](../../winscript/reference/imachinedebugmanagercookie-interface.md)
---
title: IDebugCookie (interfaz) | Microsoft Docs
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
ms.openlocfilehash: 8ee129526113a1c8af8f918de81c1f286d5cb703
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154470"
---
# <a name="idebugcookie-interface"></a>IDebugCookie (Interfaz)
Permite que la cookie de depuración se puede establecer para su uso con el `IMachineDebugManagerCookie` interfaz. Para obtener más información, consulte [IMachineDebugManagerCookie (interfaz)](../../winscript/reference/imachinedebugmanagercookie-interface.md). Esta interfaz se implementa mediante el proceso de depurar Manager (PDM) y consumida por los depuradores de scripts.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IDebugCookie` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Establece la cookie de la aplicación de depuración.|  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManagerCookie (Interfaz)](../../winscript/reference/imachinedebugmanagercookie-interface.md)
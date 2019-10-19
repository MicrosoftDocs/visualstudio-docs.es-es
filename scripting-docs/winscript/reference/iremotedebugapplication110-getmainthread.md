---
title: 'Iremotedebugapplication110 (:: GetMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff99c43f633da8454eb5fa32463886877e06ed72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574118"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Devuelve el subproceso principal para los hosts que llaman a [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439); de lo contrario, devuelve E_FAIL.  
  
> [!IMPORTANT]
> La [interfaz iremotedebugapplication (](../../winscript/reference/iremotedebugapplication-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppThread`  
 enuncia La interfaz principal de [iremotedebugapplicationthread (](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iremotedebugapplication (](../../winscript/reference/iremotedebugapplication-interface.md)  
 [IRemoteDebugApplication110 (Interfaz)](../../winscript/reference/iremotedebugapplication110-interface.md)
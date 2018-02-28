---
title: IActiveScriptSiteDebugEx (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx (Interfaz)
Implemente esta interfaz junto con el `IActiveScriptSiteDebug` si está escribiendo un host que necesita para obtener una notificación de un error en tiempo de ejecución en una aplicación y, opcionalmente, asociar a la aplicación para la depuración de la interfaz. El Administrador de procesos de depuración proporciona una notificación a través de `IActiveScriptDebug` si el depurador de scripts de un Just-In-Time no se encuentra en el equipo. Si el depurador de scripts de ningún Just-In-Time es encuentra, PDM proporciona una notificación a través de `IActiveScriptDebugEx` en su lugar.  
  
 Para obtener una notificación de un error en tiempo de ejecución, el host debe controlar [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). En función de una acción del usuario, puede, a continuación, decidir si desea adjuntar el depurador interno y se devuelve, o para devolver el inicio del depurador en el OnScriptErrorDebug `pfEnterDebugger` parámetro.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa al host un error de tiempo de ejecución de secuencia de comandos cuando el proceso de depurar Manager no encuentra a un depurador solo en tiempo externo.|
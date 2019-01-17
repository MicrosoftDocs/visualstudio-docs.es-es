---
title: IActiveScriptSiteDebugEx (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e462630f7bf52c4ca94aa59df22616e9a335a7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345882"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx (Interfaz)
Implemente esta interfaz junto con el `IActiveScriptSiteDebug` si está escribiendo un host que necesita para recibir una notificación de un error de tiempo de ejecución en una aplicación y, opcionalmente, asociar a la aplicación para la depuración de la interfaz. El Administrador de depuración de procesos proporciona una notificación a través de `IActiveScriptDebug` si el depurador de scripts de Just-In-Time se encuentra en el equipo. Si el depurador de scripts no Just-In-Time es que se encuentra el PDM proporciona una notificación a través de `IActiveScriptDebugEx` en su lugar.  
  
 Para obtener una notificación de un error de tiempo de ejecución, debe controlar el host [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). En función de una acción del usuario, puede, a continuación, decidir si desea adjuntar el depurador interno y el valor devuelto, o para devolver el inicio del depurador en el OnScriptErrorDebug `pfEnterDebugger` parámetro.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa al host un error de tiempo de ejecución de secuencia de comandos cuando el proceso de administrador de depuración no encuentra a un depurador externo de solo tiempo.|
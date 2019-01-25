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
ms.openlocfilehash: e390b610d6912de0078b817c9dfb503e5924a374
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797435"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx (Interfaz)

Implemente esta interfaz junto con el `IActiveScriptSiteDebug` si está escribiendo un host que necesita para recibir una notificación de un error de tiempo de ejecución en una aplicación y, opcionalmente, asociar a la aplicación para la depuración de la interfaz. El Administrador de depuración de procesos proporciona una notificación a través de `IActiveScriptDebug` si el depurador de scripts de Just-In-Time se encuentra en el equipo. Si el depurador de scripts no Just-In-Time es que se encuentra el PDM proporciona una notificación a través de `IActiveScriptDebugEx` en su lugar.

Para obtener una notificación de un error de tiempo de ejecución, debe controlar el host `ActiveScriptSiteDebug::OnScriptErrorDebug`. En función de una acción del usuario, puede, a continuación, decidir si desea adjuntar el depurador interno y el valor devuelto, o para devolver el inicio del depurador en el OnScriptErrorDebug `pfEnterDebugger` parámetro.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable

|Método|Descripción|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa al host un error de tiempo de ejecución de secuencia de comandos cuando el proceso de administrador de depuración no encuentra a un depurador externo de solo tiempo.|
---
title: IActiveScriptSiteWindow | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a160b17f4a46237ab78b378664a046fe8a0e7d4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345726"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Esta interfaz se implementa con los hosts que admiten una interfaz de usuario en el mismo objeto que [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Los hosts que no admiten una interfaz de usuario, como los servidores, no implementaría el `IActiveScriptSiteWindow` interfaz. El motor de scripting se tiene acceso a esta interfaz mediante una llamada a `QueryInterface` desde `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera el identificador de ventana que puede actuar como el propietario de una ventana emergente que se debe mostrar el motor de scripting.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Hace que el host habilitar o deshabilitar su ventana principal, así como los cuadros de diálogo no modal.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)
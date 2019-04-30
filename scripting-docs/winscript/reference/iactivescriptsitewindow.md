---
title: IActiveScriptSiteWindow | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3691a874121c00dcccc69958eb5746a2c1d78122
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992026"
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
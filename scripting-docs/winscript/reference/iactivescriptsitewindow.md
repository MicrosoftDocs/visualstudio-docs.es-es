---
title: IActiveScriptSiteWindow | Microsoft Docs
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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575906"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Esta interfaz la implementan los hosts que admiten una interfaz de usuario en el mismo objeto que [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Los hosts que no admiten una interfaz de usuario, como los servidores, no implementarán la interfaz `IActiveScriptSiteWindow`. El motor de scripting obtiene acceso a esta interfaz llamando a `QueryInterface` desde `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera el identificador de ventana que puede actuar como propietario de una ventana emergente que debe mostrar el motor de scripting.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Hace que el host habilite o deshabilite su ventana principal, así como los cuadros de diálogo no modales.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Interfaces)](../../winscript/reference/active-script-interfaces.md)
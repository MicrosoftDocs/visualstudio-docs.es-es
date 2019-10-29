---
title: Interfaz Iwebappdiagnosticssetup (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984542"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (Interfaz)
Esta interfaz se implementa mediante una aplicación de depuración de PDM para crear objetos COM en el proceso que se está depurando y para habilitar diagnósticos Web. Si el objeto de aplicación de depuración de PDM implementa [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), Internet Explorer llama a [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) en él una vez creado y pasa una referencia a [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Una aplicación de WWA llama a [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) y pasa en la interfaz WWA IWebApplicationHost en su lugar. Si se ha llamado a [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) con un valor distinto de NULL, [Iwebappdiagnosticssetup (::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve true. Si no es así, devuelve false y se produce un error en las llamadas a [iwebappdiagnosticssetup (:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) .  
  
> [!IMPORTANT]
> el `IWebAppDiagnosticsSetup` se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtiene los documentos de texto ocultos por el filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.|
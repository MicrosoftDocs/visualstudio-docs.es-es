---
title: IWebAppDiagnosticsSetup (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734005"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (Interfaz)
Esta interfaz se implementa una aplicación de depuración PDM para crear objetos COM en el proceso que se está depurando y para habilitar los diagnósticos de la web. Si el PDM depurar aplicación objeto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer llama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) en él después de que se ha creado y pasa una referencia a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Llama a una aplicación de WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) y pasa el WWA interfaz IWebApplicationHost en su lugar. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) se ha llamado con un valor distinto de NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve true. Si no es así, se devuelve false y se llama a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) producirá un error.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtiene los documentos de texto que están ocultos por el filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.|
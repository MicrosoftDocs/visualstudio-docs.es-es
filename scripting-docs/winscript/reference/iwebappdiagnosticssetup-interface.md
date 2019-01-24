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
ms.openlocfilehash: fc29282ec9d00ff79131765d2bf294c54fa347c6
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344907"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (Interfaz)
Esta interfaz se implementa mediante una aplicación de depuración PDM para crear objetos COM en el proceso que se está depurando y habilitar los diagnósticos de web. Si el PDM depurar aplicación objeto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer llama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) en ella una vez que se ha creado y pasa una referencia a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Llama una aplicación WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) y pasa el WWA interfaz IWebApplicationHost en su lugar. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) ha sido llamado con un valor distinto de NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve true. Si no, devuelve false y las llamadas a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) producirá un error.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtiene los documentos de texto que están ocultos por el filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.|
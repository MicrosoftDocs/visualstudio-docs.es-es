---
title: IWebAppDiagnosticsSetup (interfaz) | Documentos de Microsoft
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
ms.openlocfilehash: 71d4501fff04b62abe392c6684a4a0551dea9ee8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443665"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup (Interfaz)
Esta interfaz se implementa mediante una aplicación de depuración PDM para crear objetos COM en el proceso que se está depurando y habilitar los diagnósticos de web. Si el PDM depurar aplicación objeto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer llama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) en ella una vez que se ha creado y pasa una referencia a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Llama una aplicación WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) y pasa el WWA interfaz IWebApplicationHost en su lugar. Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) ha sido llamado con un valor distinto de NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve true. Si no, devuelve false y las llamadas a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) producirá un error.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtiene los documentos de texto que están ocultos por el filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.|
---
title: "Uso del Administrador de texto para supervisar la configuración Global | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9687e4f0be16fb42f13c6f9dd20a2cb39be50cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Uso del Administrador de texto para supervisar la configuración Global
Si implementa un editor principal, debe supervisar los cambios realizados en la configuración global, ya que estos cambios pueden afectar a la instancia del editor. Puede realizar el seguimiento de los cambios de forma escuchar los eventos generados por el Administrador de texto. Por ejemplo, cuando se especifica una preferencia global para la apariencia o comportamiento de un componente en el editor de núcleo, por ejemplo, su objeto de datos del documento, el Administrador de texto almacena esta información y comunica a todos los clientes afectados.  
  
## <a name="text-manager-functions"></a>Funciones de administrador de texto  
 El Administrador de texto genera eventos para una serie de valores, incluidos los siguientes:  
  
-   Si es un búfer en el control de código fuente  
  
-   Cómo registrarse para recibir notificaciones de cambio de archivo  
  
-   Cómo realizar un seguimiento de las vistas que están asociadas a ciertos búferes  
  
-   Preferencias de color de texto  
  
-   Pestaña frente a las preferencias de espacio  
  
 Las preferencias que son únicas para un idioma determinado no están administradas por el Administrador de texto. Esta configuración debe administrarse por cada servicio de lenguaje.  
  
 Notificación de eventos para el Administrador de texto proporcionado por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaz. Implemente esta interfaz en el cliente de objeto para controlar los eventos ha provocado el Administrador de texto. Registrar estos eventos mediante el uso de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz en el Administrador de texto.  
  
## <a name="see-also"></a>Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Características del Editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
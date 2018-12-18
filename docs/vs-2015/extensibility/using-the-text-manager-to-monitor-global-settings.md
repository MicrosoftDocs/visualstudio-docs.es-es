---
title: Con el Administrador de texto para supervisar la configuración Global | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7b53f2b4df110661ffdd0fbe0302a70d44cdc67c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808530"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Con el Administrador de texto para supervisar la configuración Global
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si implementa un editor básico, debe supervisar los cambios realizados en la configuración global, ya que estos cambios pueden afectar a la instancia del editor. Puede realizar un seguimiento de los cambios escuchando los eventos generados por el Administrador de texto. Por ejemplo, cuando se especifica una preferencia global para la apariencia o comportamiento de un componente en el editor principal, por ejemplo, su objeto de datos de documento, el Administrador de texto almacena esta información y comunica a todos los clientes afectados.  
  
## <a name="text-manager-functions"></a>Funciones de administrador de texto  
 El Administrador de texto genera eventos para una serie de valores, incluidos los siguientes:  
  
- Si un búfer está bajo control de código fuente  
  
- Cómo registrarse para recibir notificaciones de cambio de archivo  
  
- Cómo realizar un seguimiento de las vistas que están asociadas con determinados búferes  
  
- Preferencias de color de texto  
  
- Pestaña frente a las preferencias de espacio  
  
  No se administran las preferencias que son únicas para un idioma determinado por el Administrador de texto. Esta configuración debe administrarse por cada servicio de lenguaje.  
  
  Notificación de eventos para el Administrador de texto proporcionada por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaz. Implemente esta interfaz en el cliente de objeto para controlar los eventos genera el Administrador de texto. Registrar estos eventos mediante el <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz en el Administrador de texto.  
  
## <a name="see-also"></a>Vea también  
 [En el Editor básico](../extensibility/inside-the-core-editor.md)   
 [Características del Editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)


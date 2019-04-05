---
title: Con el Administrador de texto para supervisar la configuración Global | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 792c566eda53cb8a4703e8ab03982952c518d8e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988321"
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
 [Características del Editor](http://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

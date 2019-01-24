---
title: Con el Administrador de texto para supervisar la configuración Global | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 43b4f1c2de4862b30dd5822931b02292b942c50f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877555"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Use el Administrador de texto para supervisar la configuración global
Si implementa un editor básico, debe supervisar los cambios realizados en la configuración global, ya que estos cambios pueden afectar a la instancia del editor. Puede realizar un seguimiento de los cambios escuchando los eventos generados por el Administrador de texto. Por ejemplo, cuando se especifica una preferencia global para la apariencia o comportamiento de un componente en el editor principal, por ejemplo, su objeto de datos de documento, el Administrador de texto almacena esta información y comunica a todos los clientes afectados.  
  
## <a name="text-manager-functions"></a>Funciones del Administrador de texto  
 El Administrador de texto genera eventos para una serie de valores, incluidos los siguientes:  
  
- Si un búfer está bajo control de código fuente  
  
- Cómo registrarse para recibir notificaciones de cambio de archivo  
  
- Cómo realizar un seguimiento de las vistas que están asociadas con determinados búferes  
  
- Preferencias de color de texto  
  
- Pestaña frente a las preferencias de espacio  
  
  No se administran las preferencias que son únicas para un idioma determinado por el Administrador de texto. Esta configuración debe administrarse por cada servicio de lenguaje.  
  
  Notificación de eventos para el Administrador de texto proporcionada por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfaz. Implemente esta interfaz en el cliente de objeto para controlar los eventos genera el Administrador de texto. Registrar estos eventos mediante el <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz en el Administrador de texto.  
  
## <a name="see-also"></a>Vea también  
 [Dentro del editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Características del Editor](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
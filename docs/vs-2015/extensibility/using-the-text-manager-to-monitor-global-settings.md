---
title: Usar el administrador de texto para supervisar la configuración global | Microsoft Docs
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
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695470"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Uso del administrador de texto para supervisar la configuración global
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si implementa un editor básico, debe supervisar los cambios que se realizan en la configuración global, ya que estos cambios pueden afectar a la instancia del editor. Puede realizar el seguimiento de los cambios escuchando los eventos generados por el administrador de texto. Por ejemplo, cuando se especifica una preferencia global para la apariencia o el comportamiento de un componente en el editor principal, como su objeto de datos de documento, el administrador de texto almacena esta información y la comunica a todos los clientes afectados.  
  
## <a name="text-manager-functions"></a>Funciones del administrador de texto  
 El administrador de texto genera eventos para una serie de valores, entre los que se incluyen los siguientes:  
  
- Si un búfer está bajo control de código fuente  
  
- Registro de notificaciones de cambios de archivo  
  
- Cómo realizar un seguimiento de las vistas asociadas a determinados búferes  
  
- Preferencias de color de texto  
  
- Preferencias de tabulador frente a espacio  
  
  El administrador de texto no administra las preferencias que son únicas para un idioma determinado. Cada servicio de lenguaje debe administrar esta configuración.  
  
  La interfaz proporciona la notificación de eventos para el administrador de texto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> . Implemente esta interfaz en el objeto de cliente para controlar los eventos generados por el administrador de texto. Regístrese para estos eventos mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaz en el administrador de texto.  
  
## <a name="see-also"></a>Consulte también  
 [Dentro del editor principal](../extensibility/inside-the-core-editor.md)   
 [Características del editor](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

---
title: "Mediante el Administrador de texto para supervisar la configuraci&#243;n Global | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados: supervisión la configuración global"
  - "editores [Visual Studio SDK] heredados - Administrador de texto"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Mediante el Administrador de texto para supervisar la configuraci&#243;n Global
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si implementa un editor básico, debe controlar los cambios que se realizan en la Configuración global, porque estos cambios pueden afectar a la instancia del editor.  Puede seguir los cambios escuchando los eventos provocados por el administrador de texto.  Por ejemplo, cuando se especifica una preferencia global para la apariencia o el comportamiento de un componente en el editor básico, como el objeto de datos de documentos, el administrador de texto almacena esta información y la comunica a todos los clientes afectados.  
  
## Funciones de administrador de texto  
 El administrador de texto genera eventos por varios valores, incluidas las siguientes:  
  
-   si un búfer está bajo control de código fuente  
  
-   Cómo registrar para las notificaciones de archivo\-cambio  
  
-   Cómo hacer un seguimiento de las vistas son asociado a ciertos búferes  
  
-   Preferencias del color de texto  
  
-   Pestaña con preferencias de espacio  
  
 Las preferencias que son exclusivas de un lenguaje determinado no son administradas por el administrador de texto.  Estos valores se deben administrar por cada servicio de lenguaje.  
  
 La notificación de eventos para el administrador de texto proporcionan la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> .  Implemente esta interfaz en el objeto de cliente para controlar los eventos provocó el administrador de texto.  Se registra para estos eventos mediante la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> en el administrador del texto.  
  
## Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/es-es/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
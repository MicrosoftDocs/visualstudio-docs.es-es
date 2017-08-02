---
title: "C&#243;mo: agregar marcadores de texto est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - marcadores de texto estándar"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: agregar marcadores de texto est&#225;ndar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilice el siguiente procedimiento para crear uno de los tipos predeterminados de marcador de texto proporcionados el publicador de la base de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
### Para crear un marcador de texto  
  
1.  En función de si utiliza el o un sistema de coordenadas bidimensional, llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> o el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> para crear un nuevo marcador de texto.  
  
     En esta llamada al método, especifique un tipo de marcador, un intervalo de texto para crear el marcador encima, y una interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  Este método a devuelve un puntero al marcador creado recientemente de texto.  Toman a los tipos de marcador de la enumeración de <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> .  Especifique una interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> si desea ser informado eventos de marcador.  
  
    > [!NOTE]
    >  Cree marcadores de texto en el subproceso principal de la interfaz de usuario sólo.  El editor básico se basa en el contenido del búfer de texto para crear marcadores de texto y el búfer de texto no es seguro para subprocesos.  
  
## agregar un comando personalizado  
 Implementar la interfaz de `IVsTextMarkerClient` y proporcionarle un puntero de un marcador mejora comportamiento marcadores de varias maneras.  Primero, esto permite proporcionar sugerencias para el marcador y ejecutar comandos.  Esto también permite recibir notificaciones de eventos para los marcadores individuales y que cree un menú contextual personalizado sobre el marcador.  Utilice el procedimiento siguiente para agregar un comando personalizado al menú contextual de marcador.  
  
#### Para agregar un comando personalizado al menú contextual  
  
1.  Antes de que se muestre el menú contextual, el entorno llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> y le pasa un puntero al marcador de texto afectada y el número del elemento de comando del menú contextual.  
  
     Por ejemplo, los comandos punto de interrupción\-específicos en el menú contextual incluyen **quite el punto de interrupción** con **Nuevo punto de interrupción**, como se muestra en la captura de pantalla siguiente.  
  
     ![Marcador del menú contextual](~/docs/extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Pase el nuevo texto que identifica el nombre del comando personalizado.  Por ejemplo, **quite el punto de interrupción** podría ser un comando personalizado si el entorno no lo proporcionó ya.  También pasa la devuelve si el comando es compatible, disponibles y habilitado, y\/o una alternancia encendido\-apagado.  El entorno utiliza esta información para mostrar el comando personalizado en el menú contextual de la manera correcta.  
  
3.  Para ejecutar el comando, el entorno llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> , pasandole un puntero al marcador de texto y el número del comando seleccionado en el menú contextual.  
  
     Utilice esta información de esta llamada para ejecutar acciones de marcador de texto dicta el comando personalizado.  
  
## Vea también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: implementar marcadores de Error](../extensibility/how-to-implement-error-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md)
---
title: 'Cómo: agregar marcadores de texto estándar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842370"
---
# <a name="how-to-add-standard-text-markers"></a>Cómo: Agregar marcadores de texto estándar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilice el procedimiento siguiente para crear uno de los tipos de marcador de texto predeterminados que se proporcionan con el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor básico.  
  
### <a name="to-create-a-text-marker"></a>Para crear un marcador de texto  
  
1. Dependiendo de si usa un sistema de coordenadas de uno o dos dimensiones, llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para crear un nuevo marcador de texto.  
  
     En esta llamada al método, especifique un tipo de marcador, un intervalo de texto en el que se va a crear el marcador y una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz. A continuación, este método devuelve un puntero al marcador de texto que se acaba de crear. Los tipos de marcador se toman de la <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumeración. Especifique una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz si desea que se le informe de los eventos de marcador.  
  
    > [!NOTE]
    > Cree marcadores de texto solo en el subproceso de la interfaz de usuario principal. El editor básico se basa en el contenido del búfer de texto para crear marcadores de texto y el búfer de texto no es seguro para subprocesos.  
  
## <a name="adding-a-custom-command"></a>Agregar un comando personalizado  
 Implementar la `IVsTextMarkerClient` interfaz y proporcionar un puntero a ella desde un marcador mejora el comportamiento del marcador de varias maneras. En primer lugar, esto le permite proporcionar sugerencias para el marcador y ejecutar comandos. Esto también le permite recibir notificaciones de eventos para marcadores individuales y crear un menú contextual personalizado sobre el marcador. Use el procedimiento siguiente para agregar un comando personalizado al menú contextual del marcador.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Para agregar un comando personalizado al menú contextual  
  
1. Antes de que se muestre el menú contextual, el entorno llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> método y pasa un puntero al marcador de texto afectado y el número del elemento de comando en el menú contextual.  
  
     Por ejemplo, los comandos específicos del punto de interrupción en el menú contextual incluyen **quitar punto de interrupción** a través de un **nuevo punto de interrupción**, tal como se muestra en la siguiente captura de pantalla.  
  
     ![Marcador del menú contextual](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Devolver parte del texto que identifica el nombre del comando personalizado. Por ejemplo, **quitar punto de interrupción** podría ser un comando personalizado si el entorno aún no lo ha proporcionado. También se devolverá si el comando es compatible, disponible y habilitado, o si se activa o desactiva la alternancia. El entorno usa esta información para mostrar el comando personalizado en el menú contextual de la manera correcta.  
  
3. Para ejecutar el comando, el entorno llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método, pasando un puntero al marcador de texto y el número del comando seleccionado en el menú contextual.  
  
     Use esta información de esta llamada para ejecutar cualquier acción del marcador de texto que dicte el comando personalizado.  
  
## <a name="see-also"></a>Consulte también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: implementar marcadores de error](../extensibility/how-to-implement-error-markers.md)   
 [Cómo: crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)

---
title: "Cómo: agregar marcadores de texto estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bdcdbabae26a9116b1e00910ecef2f83f4075551
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-standard-text-markers"></a>Cómo: agregar marcadores de texto estándar
Utilice el procedimiento siguiente para crear uno de los tipos de marcador de texto predeterminados proporcionados con la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal.  
  
### <a name="to-create-a-text-marker"></a>Para crear un marcador de texto  
  
1.  Dependiendo de si está usando una o dos dimensiones de sistema de coordenadas, llamada la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para crear un nuevo marcador de texto.  
  
     En esta llamada al método, especifique un tipo de marcador, un intervalo de texto que se va a crear el marcador de sobre y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz. A continuación, este método devuelve un puntero al marcador de texto recién creado. Tipos de marcador se toman de la <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumeración. Especifique un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz si desea informar de eventos de marcador.  
  
    > [!NOTE]
    >  Crear marcadores de texto en el subproceso principal de interfaz de usuario. El editor básico se basa en el contenido del búfer de texto para crear marcadores de texto y el búfer de texto no es seguro para subprocesos.  
  
## <a name="adding-a-custom-command"></a>Agregar un comando personalizado  
 Implementar el `IVsTextMarkerClient` interfaz y proporcionar un puntero a él desde un marcador mejora el comportamiento de marcador de varias maneras. En primer lugar, esto le permite proporcionar sugerencias para el marcador y ejecutar comandos. Esto también permite recibir notificaciones de eventos para los marcadores individuales y para crear un menú contextual personalizado sobre el marcador. Utilice el procedimiento siguiente para agregar un comando personalizado en el menú contextual de marcador.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Para agregar un comando personalizado en el menú contextual  
  
1.  Antes de que se muestre el menú contextual, el entorno llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> método y pasa es un puntero al marcador de texto afectado y el número del elemento de comando en el menú contextual.  
  
     Por ejemplo, se incluyen los comandos específicos del punto de interrupción en el menú contextual **Quitar puntosInterrupción** a través de **nuevo punto de interrupción**, tal y como se muestra en la captura de pantalla siguiente.  
  
     ![Marcador del menú contextual](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Vuelva a pasar algún texto que identifica el nombre del comando personalizado. Por ejemplo, **Quitar puntosInterrupción** podría ser un comando personalizado si el entorno no proporcionó ya lo. Además de devolver si el comando es compatible, disponible y habilitada, o un comando alternante off. El entorno utiliza esta información para mostrar el comando personalizado en el menú contextual de la forma correcta.  
  
3.  Para ejecutar el comando, el entorno llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método, pasando un puntero para el marcador de texto y el número del comando seleccionado en el menú contextual.  
  
     Use esta información de esta llamada para ejecutar el comando personalizado dicta a las acciones de los marcadores de texto.  
  
## <a name="see-also"></a>Vea también  
 [Uso de marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: implementar marcadores de Error](../extensibility/how-to-implement-error-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md)
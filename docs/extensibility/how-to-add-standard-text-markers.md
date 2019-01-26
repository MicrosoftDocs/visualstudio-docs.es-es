---
title: Procedimiento Agregar marcadores de texto estándar | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80c32827a991a87b582f31ceefd2bfd6dbcc7a8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922355"
---
# <a name="how-to-add-standard-text-markers"></a>Procedimiento Agregar marcadores de texto estándar
Use el procedimiento siguiente para crear uno de los tipos de marcador de texto predeterminados proporcionados con la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básico.  
  
## <a name="to-create-a-text-marker"></a>Para crear un marcador de texto  
  
1.  Dependiendo de si usas un sistema de coordenadas o dos dimensiones, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para crear un nuevo marcador de texto.  
  
     En esta llamada al método, especifica un tipo de marcador, un intervalo de texto para crear el marcador a través y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz. Este método, a continuación, devuelve un puntero para el marcador de texto recién creado. Tipos de marcador se toman de la <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumeración. Especifique un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz si desea informar de eventos de marcador.  
  
    > [!NOTE]
    >  Crear marcadores de texto en el subproceso principal de la interfaz de usuario. El editor básico se basa en el contenido del búfer de texto para crear marcadores de texto y el búfer de texto no es seguro para subprocesos.  
  
## <a name="add-a-custom-command"></a>Agregar un comando personalizado  
 Implementar el `IVsTextMarkerClient` mejora la interfaz y proporcionar un puntero a él desde un marcador de comportamiento del marcador de varias maneras. En primer lugar, esto le permite proporcionar sugerencias para el marcador y ejecutar comandos. Esto también le permite recibir notificaciones de eventos para los marcadores individuales y para crear un menú contextual personalizado en el marcador. Use el procedimiento siguiente para agregar un comando personalizado en el menú contextual de marcador.  
  
### <a name="to-add-a-custom-command-to-the-context-menu"></a>Para agregar un comando personalizado al menú contextual  
  
1.  Antes de que aparezca el menú contextual, el entorno llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> método y pasa es un puntero para el marcador de texto afectado y el número del elemento de comando en el menú contextual.  
  
     Por ejemplo, se incluyen los comandos específicos de punto de interrupción en el menú contextual **quitar punto de interrupción** a través de **nuevo punto de interrupción**, como se muestra en la captura de pantalla siguiente.  
  
     ![Marcador del menú contextual](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Devolver algún texto que identifica el nombre del comando personalizado. Por ejemplo, **quitar punto de interrupción** podría ser un comando personalizado si el entorno no ya proporcionó se. Además de devolver un botón de alternancia activar / desactivar o si el comando es compatible, disponible y habilitada. El entorno usa esta información para mostrar el comando personalizado en el menú contextual de la manera correcta.  
  
3.  Para ejecutar el comando, el entorno llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método y pasa un puntero para el marcador de texto y el número del comando seleccionado en el menú contextual.  
  
     Utilice esta información de esta llamada para ejecutar el comando personalizado dicta a las acciones que sean del marcador de texto.  
  
## <a name="see-also"></a>Vea también  
 [Utilice marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: Implementar los marcadores de error](../extensibility/how-to-implement-error-markers.md)   
 [Cómo: Crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: Utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md)
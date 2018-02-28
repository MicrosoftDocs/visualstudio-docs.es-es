---
title: "Cómo: utilizar marcadores de texto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f5c5c2686bee9850da72c00e044952b15bed9c58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-text-markers"></a>Cómo: utilizar marcadores de texto
Marcadores de texto pueden aplicarse para editar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-apply-text-markers"></a>Para aplicar los marcadores de texto  
  
1.  Obtener una instancia de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> clase.  
  
    > [!NOTE]
    >  El editor de núcleo aplica automáticamente los marcadores de texto estándar a cualquier documento que está editando, y no debería ser necesario aplicar de forma explícita los marcadores de texto estándar.  
  
2.  Obtener un identificador de tipo de marcador de marcador que le interesan mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método con el `GUID` del marcador de texto que se va a trabajar con.  
  
    > [!NOTE]
    >  No utilice el `GUID` de VSPackage o del servicio que proporciona el marcador de texto.  
  
3.  Use el identificador de tipo de marcador obtenido mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método como parámetro al llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para aplicar un marcador de texto a una región determinada de texto.  
  
#### <a name="to-add-features-to-text-markers"></a>Para agregar características a los marcadores de texto  
  
1.  Puede ser deseable para agregar características adicionales a un marcador de texto, como información sobre herramientas, un menú contextual especial o un controlador para circunstancias especiales. Para ello:  
  
2.  Crear un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
3.  Si se desea una funcionalidad adicional, implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces en el mismo objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
4.  Pasar el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz que cree, a la llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método utilizado para aplicar el marcador de texto a una región determinada de texto.  
  
5.  Al agregar compatibilidad de menú contextual a una región de marcador de texto es necesario crear el menú.  
  
     Para obtener más información sobre cómo crear un menú contextual, vea [menús contextuales](../extensibility/context-menus.md).  
  
6.  El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entorno llama a los métodos de las interfaces proporcionadas, como el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> método, o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método según sea necesario.  
  
## <a name="see-also"></a>Vea también  
 [Uso de marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: implementar marcadores de Error](../extensibility/how-to-implement-error-markers.md)
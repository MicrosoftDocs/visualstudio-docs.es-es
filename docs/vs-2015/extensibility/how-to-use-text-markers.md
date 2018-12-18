---
title: 'Cómo: usar marcadores de texto | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4fea8e6d5774e8991cf70cbc84e6b713d59f199f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810212"
---
# <a name="how-to-use-text-markers"></a>Cómo: usar marcadores de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se pueden aplicar los marcadores de texto para editar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-apply-text-markers"></a>Para aplicar los marcadores de texto  
  
1.  Obtener una instancia de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> clase.  
  
    > [!NOTE]
    >  El editor básico aplica automáticamente los marcadores de texto estándar a cualquier documento que está editando, y no debería ser necesario aplicar de forma explícita los marcadores de texto estándar.  
  
2.  Obtener un identificador de tipo de marcador de los marcadores están interesados en mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método con el `GUID` del marcador de texto que desea trabajar con.  
  
    > [!NOTE]
    >  No utilice el `GUID` de VSPackage o del servicio que proporciona el marcador de texto.  
  
3.  Use el identificador de tipo de marcador obtenido mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método como parámetro al llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para aplicar un marcador de texto a una región determinada de texto.  
  
#### <a name="to-add-features-to-text-markers"></a>Para agregar características a marcadores de texto  
  
1.  Puede ser deseable para agregar características adicionales a un marcador de texto, como información sobre herramientas, un menú contextual especial o un controlador para circunstancias especiales. Para ello:  
  
2.  Crear un objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
3.  Si se desea una funcionalidad adicional, implementar el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces en el mismo objeto que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
4.  Pase el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz que cree, a la llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método utilizado para aplicar el marcador de texto a una región determinada de texto.  
  
5.  Al agregar compatibilidad de menú contextual a una región de marcador de texto es necesario crear el menú.  
  
     Para obtener más información sobre cómo crear un menú contextual, vea [menús contextuales](../extensibility/context-menus.md).  
  
6.  El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno llama a los métodos de las interfaces suministrados, como el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> método, o la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método según sea necesario.  
  
## <a name="see-also"></a>Vea también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: Implementar marcadores de error](../extensibility/how-to-implement-error-markers.md)


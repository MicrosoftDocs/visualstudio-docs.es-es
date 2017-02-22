---
title: "C&#243;mo: utilizar marcadores de texto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - uso de marcadores de texto"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: utilizar marcadores de texto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Marcadores de texto se pueden aplicar para modificar un objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## Procedimientos  
  
#### Para aplicar marcadores de texto  
  
1.  obtenga una instancia de la clase de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> .  
  
    > [!NOTE]
    >  El editor básico aplica automáticamente los marcadores de texto estándar a cualquier documento que está editando, y no debería ser necesario aplicar marcadores de texto estándar explícitamente.  
  
2.  Obtener un identificador de tipo de marcador de marcador que le interesa llamando al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> con `GUID` de marcador de texto va a trabajar.  
  
    > [!NOTE]
    >  No utilice `GUID` de VSPackage o de servicio que proporciona el marcador de texto.  
  
3.  Utilice el identificador de tipo de marcador obtenidos llamando al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> como parámetro para llamar al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> o el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> para aplicar un marcador de texto en una región determinada de texto.  
  
#### Para agregar características a marcadores de texto  
  
1.  Puede ser conveniente agregar características adicionales a un marcador de texto, como información sobre herramientas, un menú contextual especial, o controlador para las circunstancias especiales.  Para hacerlo:  
  
2.  cree un objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
3.  Si se desea que la función adicional, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>, e interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> en el mismo objeto que implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
4.  Pase la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> que crea, a la llamada al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> o al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> utilizado para aplicar el marcador de texto en una región determinada de texto.  
  
5.  Al agregar compatibilidad de menú contextual a un área de marcador de texto es necesario crear el menú.  
  
     Para obtener más información sobre cómo crear un menú contextual vea, [Menús contextuales](../extensibility/context-menus.md).  
  
6.  El entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llama a los métodos de las interfaces proporcionadas, como el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> , o el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> según sea necesario.  
  
## Vea también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: implementar marcadores de Error](../extensibility/how-to-implement-error-markers.md)
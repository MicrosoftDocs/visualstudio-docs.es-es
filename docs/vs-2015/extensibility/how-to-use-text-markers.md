---
title: 'Cómo: usar marcadores de texto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842687"
---
# <a name="how-to-use-text-markers"></a>Cómo: Usar marcadores de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los marcadores de texto se pueden aplicar para editar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-apply-text-markers"></a>Para aplicar marcadores de texto  
  
1. Obtenga una instancia de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> clase.  
  
    > [!NOTE]
    > El editor principal aplica automáticamente los marcadores de texto estándar a cualquier documento que está editando, y no debe ser necesario aplicar marcadores de texto estándar explícitamente.  
  
2. Obtenga un identificador de tipo de marcador del marcador que le interese llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método con el `GUID` del marcador de texto con el que desea trabajar.  
  
    > [!NOTE]
    > No utilice el `GUID` del VSPackage ni del servicio que proporciona el marcador de texto.  
  
3. Use el identificador de tipo de marcador obtenido llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método como un parámetro para llamar al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para aplicar un marcador de texto a una región de texto determinada.  
  
#### <a name="to-add-features-to-text-markers"></a>Para agregar características a marcadores de texto  
  
1. Puede ser deseable agregar características adicionales a un marcador de texto, como información sobre herramientas, un menú contextual especial o un controlador para circunstancias especiales. Para ello:  
  
2. Cree un objeto que implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
3. Si se desea una funcionalidad adicional, implemente las <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces y en el mismo objeto que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz.  
  
4. Pase la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz que cree, a la llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método o al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método utilizado para aplicar el marcador de texto a una región de texto determinada.  
  
5. Al agregar compatibilidad con el menú contextual a una región de marcador de texto, es necesario crear el menú.  
  
     Para obtener más información sobre cómo crear un menú contextual, vea [menús contextuales](../extensibility/context-menus.md).  
  
6. El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno llama a los métodos de las interfaces proporcionadas, como el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> método, o el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método según sea necesario.  
  
## <a name="see-also"></a>Consulte también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)   
 [Cómo: Implementar marcadores de error](../extensibility/how-to-implement-error-markers.md)

---
title: "Cómo: actualizar la barra de estado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 76801810aafa3bd4048776ca38385ad1cf508d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-status-bar"></a>Cómo: actualizar la barra de estado
El **barra de estado** es una barra de controles que se encuentra en la parte inferior de muchas ventanas de la aplicación que contiene una o varias de las líneas de texto de estado o de indicadores.  
  
### <a name="to-update-the-status-bar"></a>Para actualizar la barra de estado  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> en cada objeto de vista individuales (DocView) que proporciona el editor, como una vista de formulario y una vista de código.  
  
2.  Cuando se llama el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, actualizar la información en el **barra de estado** mediante una llamada a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo cuando se activa inicialmente la ventana del documento. En el resto del tiempo que la ventana de documento está activa, debe actualizar el **barra de estado** información como el estado de los cambios del editor.  
  
## <a name="robust-programming"></a>Programación sólida  
 A **barra de estado** contiene cuatro campos independientes:  
  
-   Texto de estado  
  
-   Barra de progreso  
  
-   Icono animado  
  
-   Información de editor  
  
 Para obtener más información, consulte [barras de estado](/cpp/mfc/status-bars).  
  
 El IDE llama automáticamente a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementación cuando se activa la ventana de documento.  
  
 El implementador de VSPackage es responsable de actualizar el texto de estado en la barra de estado. El IDE restablece esta cadena a "Listo" si el campo de texto de estado se establece en el texto vacío ("") en tiempo de inactividad.  
  
## <a name="see-also"></a>Vea también  
 [Barras de estado](/cpp/mfc/status-bars)
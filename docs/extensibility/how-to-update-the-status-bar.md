---
title: "C&#243;mo: actualizar la barra de estado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - actualización la barra de estado"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: actualizar la barra de estado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**barra de estado** es una barra de controles situada en la parte inferior de muchas ventanas de la aplicación que contiene una o más líneas o marcas de texto de estado.  
  
### para actualizar la barra de estado  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> en cada objeto de vista individual \(DocView\) que el editor proporciona, como una vista de formulario y una vista código.  
  
2.  Si el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, actualice la información de **barra de estado** llamando a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  El IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> sólo cuando la ventana de documento se provoca inicialmente.  Para el resto de tiempo que la ventana de documento activo, debe actualizar la información de **barra de estado** como el estado del editor.  
  
## Programación eficaz  
 **barra de estado** contiene cuatro campos independientes:  
  
-   Texto de estado  
  
-   Progress Bar  
  
-   icono animado  
  
-   Información del editor  
  
 Para obtener más información, vea [Barras de estado](/visual-cpp/mfc/status-bars).  
  
 El IDE llama automáticamente al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> de implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> cuando se activa la ventana de documento.  
  
 El implementador de VSPackage es responsable de actualizar el texto de estado en la barra de estado.  El IDE restablece esta cadena a " listo " si el campo de texto del estado se establece para vaciar el texto \(""\) en el tiempo de inactividad.  
  
## Vea también  
 [Barras de estado](/visual-cpp/mfc/status-bars)
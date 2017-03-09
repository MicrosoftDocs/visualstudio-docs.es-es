---
title: "C&#243;mo: Leer la regi&#243;n de comentarios de la barra de estado y escribir en ella | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "región de comentarios, barra de estado"
  - "barra de estado, región de comentarios"
  - "barra de estado, información general"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# C&#243;mo: Leer la regi&#243;n de comentarios de la barra de estado y escribir en ella
La región de comentarios de muestra de la barra de estado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] manda texto.  Puede establecer y recuperar texto, texto estático de la pantalla, y resalta el texto mostrado.  
  
### Para utilizar la región de comentarios de la barra de estado de Visual Studio  
  
1.  Obtenga una instancia de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , que está disponible con el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Determine si la barra de estado es inmovilizada llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> de la instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> .  
  
3.  Establezca el texto de la región de comentarios llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A> y pasando una cadena de texto.  
  
4.  Leer el texto de la región de comentarios llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> .  
  
## Ejemplo  
 Este ejemplo muestra cómo escribir texto en y leer el texto de la región de comentarios.  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 En el ejemplo anterior, el código realiza las siguientes operaciones:  
  
-   Obtiene una instancia de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
-   Comprueba si la barra de estado es inmovilizada llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> .  
  
-   Deshabilita otras actualizaciones en la barra de estado llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> .  
  
-   Lee el texto de la barra de estado llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> y lo muestra en un cuadro de mensaje.  
  
-   Permite actualizaciones en la barra de estado llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> y pasar 0 en el parámetro.  
  
-   Borra el contenido de la barra de estado llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> .  
  
## Vea también  
 [Ampliación de la barra de estado](../extensibility/extending-the-status-bar.md)   
 [Cómo: Programar el área de la barra de progreso de la barra de estado](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Cómo: Usar la región de animación de la barra de estado](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Cómo: Programar la región del diseñador de la barra de estado](../misc/how-to-program-the-designer-region-of-the-status-bar.md)
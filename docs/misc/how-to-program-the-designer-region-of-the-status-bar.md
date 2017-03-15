---
title: "C&#243;mo: Programar la regi&#243;n del dise&#241;ador de la barra de estado | Microsoft Docs"
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
  - "región de diseñador, barra de estado"
  - "barras de estado, programar"
  - "barras de estado, región de diseñador"
ms.assetid: 735a86bb-80b2-4557-9677-00799856017f
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# C&#243;mo: Programar la regi&#243;n del dise&#241;ador de la barra de estado
La región del diseñador de la barra de estado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra la información relativa a editar, por ejemplo, el número de línea o el número de columnas de la ubicación del cursor.  
  
### Programar la región del diseñador de la barra de estado de Visual Studio  
  
1.  Obtenga una instancia de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , que está disponible con el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Actualice la región del diseñador de la barra de estado llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetInsMode%2A> y el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetLineColChar%2A> de la instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> .  
  
## Ejemplo  
 Este ejemplo muestra cómo programar la región del diseñador de la barra de estado.  
  
 [!code-vb[VSSDKDesignerStatusBar#1](../misc/codesnippet/VisualBasic/how-to-program-the-designer-region-of-the-status-bar_1.vb)]
 [!code-cs[VSSDKDesignerStatusBar#1](../misc/codesnippet/CSharp/how-to-program-the-designer-region-of-the-status-bar_1.cs)]  
  
## Vea también  
 [Ampliación de la barra de estado](../extensibility/extending-the-status-bar.md)   
 [Cómo: Leer la región de comentarios de la barra de estado y escribir en ella](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Cómo: Programar el área de la barra de progreso de la barra de estado](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Cómo: Usar la región de animación de la barra de estado](../misc/how-to-use-the-animation-region-of-the-status-bar.md)
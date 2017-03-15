---
title: "C&#243;mo: Programar el &#225;rea de la barra de progreso de la barra de estado | Microsoft Docs"
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
  - "barra de estado, área de la barra de progreso"
  - "barra de progreso, barra de estado"
  - "barra de estado, programar"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# C&#243;mo: Programar el &#225;rea de la barra de progreso de la barra de estado
La región de la barra de progreso de la barra de estado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra el progreso incremental de las operaciones rápidas, por ejemplo, guardar un archivo en el disco.  
  
### para utilizar la región de la barra de progreso de la barra de estado de Visual Studio  
  
1.  Obtenga una instancia de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , que está disponible con el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Inicializa la barra de progreso a iniciar valores llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> .  
  
3.  Actualice la barra de progreso como la operación continúa utilizando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> para establecer nuevos valores.  
  
## Ejemplo  
 Este ejemplo muestra cómo inicializar y actualizar la barra de progreso.  
  
 [!code-cs[VSSDKProgressStatusBar#1](../misc/codesnippet/CSharp/how-to-program-the-progress-bar-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKProgressStatusBar#1](../misc/codesnippet/VisualBasic/how-to-program-the-progress-bar-region-of-the-status-bar_1.vb)]  
  
 en el ejemplo, el código:  
  
-   Obtiene una instancia de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
-   Inicializa la barra de progreso determinada iniciar valores llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> .  
  
-   Simula una operación recorriendo en iteración de un bucle de `for` y actualiza los valores de la barra de progreso mediante el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> .  
  
-   Borra la barra de progreso mediante el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> .  
  
## Vea también  
 [Ampliación de la barra de estado](../extensibility/extending-the-status-bar.md)   
 [Cómo: Leer la región de comentarios de la barra de estado y escribir en ella](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Cómo: Usar la región de animación de la barra de estado](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Cómo: Programar la región del diseñador de la barra de estado](../misc/how-to-program-the-designer-region-of-the-status-bar.md)
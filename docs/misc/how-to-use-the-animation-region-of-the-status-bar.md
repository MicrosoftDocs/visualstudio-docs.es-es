---
title: "C&#243;mo: Usar la regi&#243;n de animaci&#243;n de la barra de estado | Microsoft Docs"
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
  - "barra de estado, programar"
  - "barra de estado, región de animación"
  - "región de animación, barra de estado"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# C&#243;mo: Usar la regi&#243;n de animaci&#243;n de la barra de estado
La región de la animación de barra de estado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra una animación de Bucle que indica una operación larga o una operación de longitud indeterminada \(por ejemplo, compilar varios proyectos en una solución\).  
  
### Para utilizar la región de la animación de barra de estado de Visual Studio  
  
1.  Obtenga una instancia de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> , que está disponible con el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> .  
  
2.  Inicie la aplicación llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> de barra de estado.  Paso en 1 como valor del primer parámetro, y una referencia a un icono animado como valor del segundo parámetro.  
  
3.  Detenga la aplicación llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> de barra de estado.  Paso en 0 como valor del primer parámetro, y una referencia al icono animado como valor del segundo parámetro.  
  
## Ejemplo  
 Este ejemplo muestra cómo ejecutar una animación integrada en la región de la animación.  
  
 [!CODE [VSSDKAnimationStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkanimationstatusbar#1)]  
  
## Vea también  
 [Ampliación de la barra de estado](../extensibility/extending-the-status-bar.md)   
 [Cómo: Leer la región de comentarios de la barra de estado y escribir en ella](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Cómo: Programar el área de la barra de progreso de la barra de estado](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Cómo: Programar la región del diseñador de la barra de estado](../misc/how-to-program-the-designer-region-of-the-status-bar.md)
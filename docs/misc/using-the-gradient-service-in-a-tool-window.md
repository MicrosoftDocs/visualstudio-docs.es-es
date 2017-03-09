---
title: "Uso del servicio de degradado en una ventana de herramientas | Microsoft Docs"
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
  - "servicios, tutoriales"
  - "ventanas de herramientas, servicio de degradado"
  - "servicio de degradado, tutoriales"
  - "servicios, consumir"
ms.assetid: 67590982-6e1f-4e4b-be18-7d1b294cabff
caps.latest.revision: 44
caps.handback.revision: 44
manager: "douge"
---
# Uso del servicio de degradado en una ventana de herramientas
Dado que las ventanas de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se compilan con Windows \(WPF\) presentation foundation, no tiene que llamar al servicio de degradado en código.  En su lugar, del diseñador que representa la superficie de la ventana de herramientas, seleccione el elemento de `StackPanel` y, a continuación, en la ventana de **Propiedades** , modifique la propiedad de **Fondo** para establecer el degradado.  Para obtener más información, vea [Establecer colores, degradados y opacidad](../misc/setting-colors-gradients-and-opacity.md).  
  
## Vea también  
 [NOT IN BUILD: Tool Window Walkthroughs](http://msdn.microsoft.com/es-es/ecffc579-0e96-48ad-90f3-01a3d80f3ce5)   
 [Extender ventanas de herramientas](../misc/extending-tool-windows.md)   
 [Establecer colores, degradados y opacidad](../misc/setting-colors-gradients-and-opacity.md)
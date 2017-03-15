---
title: "C&#243;mo: hospedar un Editor en otro Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - hospedan un editor anidado"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: hospedar un Editor en otro Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En Visual Studio puede dentro de otra del editor de hospedar uno especificando la ventana que hospeda como ventana primaria.  Para ello, establezca los parámetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> en el cuadro de la ventana secundaria.  
  
### Para configurar el marco de la ventana para hospedar un editor  
  
1.  Seleccione un editor como editor hospedado creando un panel de ventana secundaria.  
  
     Este panel es donde se escribirá el texto del editor.  
  
2.  Cree el editor de hospedaje mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> o el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
3.  Establezca las propiedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> y de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> en la aplicación de la ventana del editor hospedado pasando estas propiedades como parámetros al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> , respectivamente.  
  
     Si necesita recuperar estos parámetros, pase estas propiedades en el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .  
  
4.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> para el editor contenido.  
  
     El editor aparece en el panel hospedado de editor que contiene.  
  
## Programación eficaz  
 **Diseñador de aplicaciones** en Visual Studio Team Edition para Architects es un ejemplo de un marco de la ventana del editor que hospeda otro editor.  Los hosts de **Diseñador de aplicaciones** otros diseñadores en el panel derecho.  Agrega un panel del diseñador \(o la página de **Propiedades** \) para cada uno de los diseñadores contenido al marco de la ventana que contiene.
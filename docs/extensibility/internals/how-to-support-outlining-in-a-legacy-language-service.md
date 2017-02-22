---
title: "C&#243;mo: admitir la esquematizaci&#243;n en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], contraer los comandos de definiciones"
  - "Servicios de lenguaje, compatibles con contraer al comando de definiciones"
  - "texto oculto, contraer al comando de definiciones"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: admitir la esquematizaci&#243;n en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esquematización se utiliza para expandir o contraer las diferentes áreas de texto. Se utiliza el modo de esquematización puede definirse de manera distinta en diferentes idiomas. Para obtener más información, consulta [Esquematización](../../ide/outlining.md).  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma de implementar la esquematización, consulte [Tutorial: esquematización](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 A continuación muestra cómo admitir este comando para el servicio de lenguaje.  
  
### Para admitir la esquematización  
  
1.  Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> en el objeto de servicio de lenguaje.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> en el objeto de sesión de esquema actual para agregar nuevas regiones de esquema.  
  
## Programación eficaz  
 Cuando un usuario selecciona **Contraer a definiciones** en el **esquematización** menú, las llamadas IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> en su servicio de lenguaje.  
  
 Cuando se llama a este método, el IDE se pasa en un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntero \(un puntero a un búfer de texto\) y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> \(un puntero a la sesión actual de esquematización\).  
  
 Puede llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> método para varias regiones de esquema mediante la especificación de estas regiones en el `rgOutlnReg` parámetro. El `rgOutlnReg` parámetro es un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> estructura. Este proceso le permite especificar distintas características de la región oculta, por ejemplo, si se expande o contrae una región determinada.  
  
> [!NOTE]
>  Tenga cuidado sobre la ocultación de caracteres de nueva línea. Texto oculto debe abarcar desde el principio de la primera línea hasta el último carácter de la última línea en una sección, dejando el último carácter de nueva línea visible.  
  
## Vea también  
 [Cómo: proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Cómo: proporcionar soporte ampliado de esquematización en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
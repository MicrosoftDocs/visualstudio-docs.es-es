---
title: "Implementaci&#243;n de colores de sintaxis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sintaxis de color, implementar"
  - "editores [Visual Studio SDK], colorear texto"
  - "texto, colorear en editores"
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Implementaci&#243;n de colores de sintaxis
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando el servicio de lenguaje proporciona colores de sintaxis, el analizador convierte una línea de texto en una matriz de elementos coloreables y devuelve los tipos de token correspondientes a estos elementos coloreables. El analizador debe devolver tipos de token que pertenecen a una lista de elementos coloreables.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra cada elemento coloreable en la ventana de código según los atributos asignados por el objeto de aplicador de color para el tipo de token adecuado.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Especifica una interfaz de analizador, y la implementación del analizador es decisión suya. Sin embargo, se proporciona una implementación de analizador predeterminada en el proyecto del paquete de idioma de Visual Studio. Código administrado, el marco de trabajo de paquete administrado \(MPF\) proporciona total compatibilidad para colorear el texto.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información acerca de la nueva forma para implementar los colores de sintaxis, consulte [Tutorial: Resaltar texto](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## Pasos seguidos por un Editor para colorear el texto  
  
1.  El editor Obtiene el aplicador de color mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> objeto.  
  
2.  Las llamadas de editor el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> método para determinar si el aplicador de color es el estado de cada línea para mantenerse fuera del aplicador de color.  
  
3.  Si el aplicador de color requiere el estado que se mantienen fuera del aplicador de color, el editor llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> método para obtener el estado de la primera línea.  
  
4.  Para cada línea en el búfer, se llama el editor de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método, que realiza los pasos siguientes:  
  
    1.  La línea de texto se pasa a un escáner para convertir el texto en tokens. Cada token especifica el texto del token y el tipo de token.  
  
    2.  El tipo de token se convierte en un índice en una lista de elementos coloreable.  
  
    3.  La información del token se utiliza para rellenar una matriz tal que cada elemento de la matriz corresponde a un carácter en la línea. Los valores almacenados en la matriz son los índices en la lista de elementos coloreable.  
  
    4.  Se devuelve el estado al final de la línea para cada línea.  
  
5.  Si el aplicador de color requiere el mantenimiento del estado, el editor se almacena en caché el estado de esa línea.  
  
6.  El editor representa la línea de texto con la información devuelta por la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> \(método\). Para ello, siga estos pasos:  
  
    1.  Para cada carácter de la línea, obtener el índice del elemento coloreable.  
  
    2.  Si utiliza los elementos predeterminados del coloreable, tener acceso a lista coloreable del editor.  
  
    3.  De lo contrario, llamar al servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método para obtener un elemento coloreable.  
  
    4.  Utilice la información de elemento coloreable para representar el texto en la pantalla.  
  
## Aplicador de color Managed Package Framework  
 El marco de trabajo de paquete administrado \(MPF\) proporciona todas las clases necesitan para implementar un aplicador de color. La clase de servicio de lenguaje debe heredar la <xref:Microsoft.VisualStudio.Package.LanguageService> clase e implemente los métodos necesarios. Debe proporcionar un escáner y el analizador mediante la implementación de la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz y devolver una instancia de la interfaz de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> \(método\) \(uno de los métodos que deben implementarse en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase\). Para obtener más información, consulta [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## Vea también  
 [Cómo: usar elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
---
title: "Extender ventanas de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas [SDK de Visual Studio], herramientas"
  - "ventanas de documento"
  - "ventanas de herramientas"
  - "ventanas [SDK de Visual Studio], documento"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# Extender ventanas de herramientas
Las ventanas de herramientas de Visual Studio son, en general, ventanas de solo lectura que no están basadas en archivos. En esto se diferencian de las ventanas de documento, que muestran archivos en modo de lectura y escritura. Las ventanas **Cuadro de herramientas**, **Explorador de soluciones**, **Propiedades** y el **Explorador web** son ejemplos de ventanas de herramientas.  
  
 Todas las ventanas de herramientas en Visual Studio 2010 y versiones posteriores están basadas en WPF. En las versiones de Visual Studio anteriores a Visual Studio 2010, las ventanas de herramientas se basaban en Windows Forms. Todavía se pueden mostrar ventanas basadas en Windows Forms, pero las nuevas ventanas de herramientas deben estar basadas en WPF.  
  
## Fundamentos de la ventana de herramientas  
 Para proporcionar una ventana de herramientas, debe registrarla en Visual Studio y especificar su ubicación y tamaño predeterminados. Para obtener más información, consulta [Ventanas de herramientas en el registro](../extensibility/tool-windows-in-the-registry.md).  
  
 Normalmente, las ventanas de herramientas se crean o se abren haciendo clic en un comando de menú. Para crear una ventana de herramientas mediante programación, vea [Abrir una ventana de herramientas mediante programación](../misc/opening-a-tool-window-programmatically.md).  
  
 Las ventanas de herramientas son de instancia única de forma predeterminada, lo que significa que solo una instancia de la ventana de herramientas puede estar abierta a la vez. Cuando se abre una ventana de herramientas de instancia única, permanece abierta hasta que se cierra el IDE. Al hacer clic en el botón Cerrar de una ventana de herramientas de instancia única, se cambia solo su visibilidad. También puede crear ventanas de herramientas de varias instancias, de forma que varias instancias de la ventana puedan abrir simultáneamente. Vea [Creación de una ventana de herramienta de instancias múltiples](../extensibility/creating-a-multi-instance-tool-window.md) para obtener más información.  
  
 Las ventanas de herramientas se pueden acoplar, ser flotantes o con pestañas en el marco del documento. El IDE proporciona el marco de ventana de herramientas y se usa para controlar el tamaño, la ubicación, el estado de acoplamiento y otras propiedades persistentes. El panel de la ventana de herramientas muestra el contenido. La ubicación y tamaño predeterminados se aplican solo cuando la ventana de herramientas se abre por primera vez; después se guarda el estado de la ventana de herramientas.  
  
 Los paneles de la ventana de herramientas pueden hospedar controles de usuario WPF y admiten barras de herramientas. Puede invalidar la propiedad <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> para devolver el identificador del control hospedado.  
  
 Las ventanas de herramientas pueden ser *dinámicas* \(también conocidas como *visibles automáticamente*\). Las ventanas de herramientas dinámicas están visibles siempre que se aplica su contexto relacionado de interfaz de usuario. El uso de la visibilidad automática puede reducir la cantidad de ventanas en el IDE. Para obtener más información, consulta [Abrir una ventana de herramientas dinámica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Los VSPackages no son la única manera de crear una ventana de herramientas. Los complementos pueden crear una ventana de herramientas mediante el modelo de automatización de Visual Studio. Para obtener más información, consulta [Cómo: Crear y controlar ventanas de herramientas](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md).  
  
## Vea también  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [Ventanas de documento](../extensibility/internals/document-windows.md)   
 [Agregar búsqueda a una ventana de herramientas](../extensibility/adding-search-to-a-tool-window.md)
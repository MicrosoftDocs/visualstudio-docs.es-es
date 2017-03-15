---
title: "C&#243;mo: Escribir un visualizador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, visualizadores"
  - "visualizadores, escribir"
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# C&#243;mo: Escribir un visualizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede escribir un visualizador personalizado para un objeto de cualquier clase administrada, excepto <xref:System.Object> o <xref:System.Array>.  
  
> [!NOTE]
>  En las aplicaciones de la **Tienda**, solo se admiten los visualizadores de texto estándar, HTML, XML y JSON.  No se admiten los visualizadores personalizados \(creados por el usuario\).  
  
 La arquitectura de un visualizador del depurador tiene dos partes:  
  
-   El *lado depurador* se ejecuta dentro del depurador de Visual Studio.  El código del lado depurador crea y muestra la interfaz de usuario para el visualizador.  
  
-   El *lado depurado* se ejecuta dentro del proceso que Visual Studio depura \(el *depurado*\).  
  
 El objeto de datos que desea visualizar \(un objeto String, por ejemplo\) existe en el proceso depurado.  Por lo tanto, el lado depurado tiene que enviar el objeto de datos al lado depurador, que después puede mostrarlo mediante la interfaz de usuario creada.  
  
 El lado depurador recibe este objeto de datos que se visualizará desde un *proveedor de objeto* que implementa la interfaz <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>.  El lado depurado envía el objeto de datos a través del *origen de objeto*, el cual se deriva de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  El proveedor de objetos también puede devolver los datos al origen del objeto, lo que permite escribir un visualizador que edite datos, además de mostrarlos.  El proveedor de objetos puede ser reemplazado para comunicarse con el evaluador de expresiones y, por consiguiente, con el origen del objeto.  
  
 El lado depurado y el lado depurador se comunican entre sí a través de <xref:System.IO.Stream>.  Se proporcionan métodos para serializar un objeto de datos en <xref:System.IO.Stream> y deserializar <xref:System.IO.Stream> en un objeto de datos.  
  
 El código del lado depurado se especifica utilizando el atributo DebuggerVisualizer \(<xref:System.Diagnostics.DebuggerVisualizerAttribute>\).  
  
 Para crear la interfaz de usuario del visualizador en el lado depurador, es necesario crear una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> y reemplazar el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar la interfaz.  
  
 Puede utilizar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios Windows Forms, cuadros de diálogo y controles desde el visualizador.  
  
 La compatibilidad con los tipos genéricos es limitada.  Puede escribir un visualizador para un destino que sólo es un tipo genérico si el tipo genérico es un tipo abierto.  Esta restricción es igual que la restricción de uso del atributo `DebuggerTypeProxy`.  Para obtener información detallada, vea [Utilizar el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Los visualizadores personalizados pueden tener consideraciones de seguridad.  Vea [Consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md).  
  
 Los siguientes procedimientos proporcionan una visión de alto nivel de los pasos necesarios para crear un visualizador.  Para una explicación más detallada, vea [Tutorial: Escribir un visualizador en C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### Para crear el lado depurador  
  
1.  Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obtener el objeto visualizado en el lado depurador.  
  
2.  Cree una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Reemplace el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar su interfaz.  Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios Windows Forms, cuadros de diálogo y controles como parte de la interfaz.  
  
4.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\).  
  
### Para crear el lado depurado  
  
1.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\) y un origen de objeto \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>\).  Si omite el origen del objeto, se utilizará un origen de objeto predeterminado.  
  
2.  Si desea que el visualizador pueda editar y mostrar objetos de datos, además de mostrarlos, será necesario invalidar los métodos `TransferData` o `CreateReplacementObject` de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## Vea también  
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Cómo: Comprobar y depurar un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md)
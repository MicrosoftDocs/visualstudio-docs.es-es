---
title: Filtrar Escribir un visualizador | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2421121e343fabbe3f2ec7d88ec087c6b84c8709
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988836"
---
# <a name="how-to-write-a-visualizer"></a>Filtrar Escribir un visualizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede escribir un visualizador personalizado para un objeto de cualquier clase administrada, excepto <xref:System.Object> o <xref:System.Array>.  
  
> [!NOTE]
>  En **Store** aplicaciones, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
 La arquitectura de un visualizador del depurador tiene dos partes:  
  
- El *lado depurador* se ejecuta dentro del depurador de Visual Studio. El código del lado depurador crea y muestra la interfaz de usuario para el visualizador.  
  
- El *lado depurado* se ejecuta dentro del proceso que Visual Studio depura (el *depurado*).  
  
  El objeto de datos que desea visualizar (un objeto String, por ejemplo) existe en el proceso depurado. Por lo tanto, el lado depurado tiene que enviar el objeto de datos al lado depurador, que después puede mostrarlo mediante la interfaz de usuario creada.  
  
  El lado depurador recibe este objeto de datos que se visualizará desde un *proveedor de objetos* que implementa el <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfaz. El lado depurado envía el objeto de datos a través de la *origen del objeto*, que se deriva de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. El proveedor de objetos también puede devolver los datos al origen del objeto, lo que permite escribir un visualizador que edite datos, además de mostrarlos. El proveedor de objetos puede ser reemplazado para comunicarse con el evaluador de expresiones y, por consiguiente, con el origen del objeto.  
  
  El lado depurado y el lado depurador se comunican entre sí a través de <xref:System.IO.Stream>. Se proporcionan métodos para serializar un objeto de datos en <xref:System.IO.Stream> y deserializar <xref:System.IO.Stream> en un objeto de datos.  
  
  El código del lado depurado se especifica utilizando el atributo DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
  Para crear la interfaz de usuario del visualizador en el lado depurador, es necesario crear una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> y reemplazar el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar la interfaz.  
  
  Puede utilizar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios Windows Forms, cuadros de diálogo y controles desde el visualizador.  
  
  La compatibilidad con los tipos genéricos es limitada. Puede escribir un visualizador para un destino que sólo es un tipo genérico si el tipo genérico es un tipo abierto. Esta restricción es igual que la restricción de uso del atributo `DebuggerTypeProxy`. Para obtener más información, consulte [utilizando el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Los visualizadores personalizados pueden tener consideraciones de seguridad. Consulte [consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md).  
  
  Los siguientes procedimientos proporcionan una visión de alto nivel de los pasos necesarios para crear un visualizador. Para obtener una explicación más detallada, consulte [Tutorial: Escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Para crear el lado depurador  
  
1.  Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obtener el objeto visualizado en el lado depurador.  
  
2.  Cree una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Reemplace el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar su interfaz. Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios Windows Forms, cuadros de diálogo y controles como parte de la interfaz.  
  
4.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Para crear el lado depurado  
  
1.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) y un origen de objeto (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Si omite el origen del objeto, se utilizará un origen de objeto predeterminado.  
  
2.  Si desea que el visualizador pueda editar y mostrar objetos de datos, además de mostrarlos, será necesario invalidar los métodos `TransferData` o `CreateReplacementObject` de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## <a name="see-also"></a>Vea también  
 [Creación de visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Instalación de un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Cómo: Probar y depurar un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md)

---
title: Crear los visualizadores personalizados de datos | Documentos de Microsoft
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec31ea837c78fc1d47c3df02d129ac3c5f4f3657
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-visualizers-of-data"></a>Crear los visualizadores personalizados de datos
 Los visualizadores son componentes de la [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interfaz de usuario del depurador. A *visualizador* crea un cuadro de diálogo u otra interfaz para mostrar una variable o un objeto de forma que se ajuste a su tipo de datos. Por ejemplo, un visualizador HTML interpreta una cadena HTML y muestra el resultado tal como aparecería en una ventana del explorador; un visualizador de mapa de bits interpreta una estructura de mapa de bits y muestra el gráfico que representa. Algunos visualizadores permiten modificar y ver los datos.

 El depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] incluye seis visualizadores estándar. Estos son los de texto, HTML, XML y JSON visualizadores, todos ellos funcionan en objetos de cadena; el visualizador de árboles de WPF, para mostrar las propiedades de un árbol visual de objetos WPF; y el visualizador del conjunto de datos, que funciona con objetos DataSet, DataView y DataTable. Es posible que, en el futuro, haya visualizadores adicionales disponibles para descargar de Microsoft Corporation, de terceros y de la comunidad. También puede escribir sus propios visualizadores e instalarlos en el depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

 > [!NOTE]
 > Para crear un visualizador personalizado para código nativo, consulte el [visualizador del depurador nativo de SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) ejemplo. En las aplicaciones UWP y Windows 8.x, no se admiten los visualizadores personalizados.

 En el depurador, los visualizadores se representan mediante un icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador"). Cuando aparezca el icono de lupa en una **información sobre datos**, en una ventana del depurador como el **inspección** ventana, o en la **Inspección rápida** cuadro de diálogo, puede hacer clic en la lupa para Seleccione un visualizador adecuado para el tipo de datos del objeto correspondiente.

## <a name="overview-of-custom-visualizers"></a>Información general sobre los visualizadores personalizados

Puede escribir un visualizador personalizado para un objeto de cualquier clase administrada, excepto <xref:System.Object> o <xref:System.Array>.  
  
 La arquitectura de un visualizador del depurador tiene dos partes:  
  
-   El *lado depurador* se ejecuta dentro del depurador de Visual Studio. El código del lado depurador crea y muestra la interfaz de usuario para el visualizador.  
  
-   El *lado depurado* se ejecuta dentro del proceso que Visual Studio depura (el *depurado*).  
  
 El objeto de datos que desea visualizar (un objeto String, por ejemplo) existe en el proceso depurado. Por lo tanto, el lado depurado tiene que enviar el objeto de datos al lado depurador, que después puede mostrarlo mediante la interfaz de usuario creada.  
  
 El lado depurador recibe este objeto de datos que se visualizará desde un *proveedor de objetos* que implementa el <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfaz. El lado depurado envía el objeto de datos a través de la *origen del objeto*, que se deriva de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. El proveedor de objetos también puede devolver los datos al origen del objeto, lo que permite escribir un visualizador que edite datos, además de mostrarlos. El proveedor de objetos puede ser reemplazado para comunicarse con el evaluador de expresiones y, por consiguiente, con el origen del objeto.  
  
 El lado depurado y el lado depurador se comunican entre sí a través de <xref:System.IO.Stream>. Se proporcionan métodos para serializar un objeto de datos en <xref:System.IO.Stream> y deserializar <xref:System.IO.Stream> en un objeto de datos.  
  
 El código del lado depurado se especifica utilizando el atributo DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
 Para crear la interfaz de usuario del visualizador en el lado depurador, es necesario crear una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> y reemplazar el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar la interfaz.  
  
 Puede utilizar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios Windows Forms, cuadros de diálogo y controles desde el visualizador.  
  
 La compatibilidad con los tipos genéricos es limitada. Puede escribir un visualizador para un destino que sólo es un tipo genérico si el tipo genérico es un tipo abierto. Esta restricción es igual que la restricción de uso del atributo `DebuggerTypeProxy`. Para obtener más información, consulte [utilizando el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Los visualizadores personalizados pueden tener consideraciones de seguridad. Vea [consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md).  
  
 Los siguientes procedimientos proporcionan una visión de alto nivel de los pasos necesarios para crear un visualizador. Para obtener una explicación más detallada, vea [Tutorial: escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Para crear el lado depurador  
  
1.  Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obtener el objeto visualizado en el lado depurador.  
  
2.  Cree una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Reemplace el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar su interfaz. Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios Windows Forms, cuadros de diálogo y controles como parte de la interfaz.  
  
4.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Para crear el lado depurado  
  
1.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) y un origen de objeto (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Si omite el origen del objeto, se utilizará un origen de objeto predeterminado.  
  
2.  Si desea que el visualizador pueda editar y mostrar objetos de datos, además de mostrarlos, será necesario invalidar los métodos `TransferData` o `CreateReplacementObject` de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="in-this-section"></a>En esta sección
  
 [Tutorial: Escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Tutorial: Escribir un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Cómo: Comprobar y depurar un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referencia de la API del visualizador](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
---
title: Creación de visualizadores de datos personalizado | Microsoft Docs
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048955"
---
# <a name="create-custom-data-visualizers"></a>Creación de visualizadores de datos personalizados
 Un *visualizador* forma parte de la [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interfaz de usuario del depurador que muestra una variable o un objeto de forma adecuada según su tipo de datos. Por ejemplo, un visualizador HTML interpreta una cadena HTML y muestra el resultado tal como aparecería en una ventana del explorador. Un visualizador de mapa de bits interpreta una estructura de mapa de bits y muestra el gráfico que representa. Algunos visualizadores permiten modificar así como ver los datos.

 El depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] incluye seis visualizadores estándar. El texto, HTML, XML y JSON visualizadores funcionan en objetos de cadena. El visualizador de árboles de WPF muestra las propiedades de un árbol visual de objetos WPF. El visualizador del conjunto de datos funciona con objetos DataSet, DataView y DataTable.

Los visualizadores más pueden estar disponibles para su descarga de Microsoft, terceros y la Comunidad. También puede escribir sus propios visualizadores e instalarlos en el [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] depurador.

En el depurador, un visualizador se representa mediante un icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador"). Puede seleccionar el icono en una **información sobre datos**, depurador **inspección** ventana, o **Inspección rápida** cuadro de diálogo y, a continuación, seleccione el visualizador adecuado para el objeto correspondiente.

## <a name="write-custom-visualizers"></a>Escribir los visualizadores personalizados

 > [!NOTE]
 > Para crear un visualizador personalizado para código nativo, vea el [visualizador del depurador nativo SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) ejemplo. No se admiten los visualizadores personalizados para las aplicaciones UWP y Windows 8.x.

Puede escribir un visualizador personalizado para un objeto de cualquier clase administrada, excepto <xref:System.Object> o <xref:System.Array>.

La arquitectura de un visualizador del depurador tiene dos partes:

- El *lado depurador* se ejecuta en el depurador de Visual Studio y crea y muestra la interfaz de usuario del visualizador.

- El *lado depurado* se ejecuta dentro del proceso que Visual Studio depura (el *depurado*). El objeto de datos para visualizar (por ejemplo, un objeto de cadena) existe en el proceso depurado. El lado depurado envía el objeto en el lado depurador, que se muestra en la interfaz de usuario creada.

El lado depurador recibe el objeto de datos desde un *proveedor de objetos* que implementa el <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfaz. El lado depurado envía el objeto a través de la *origen del objeto*, que se deriva de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

El proveedor de objetos también puede enviar datos de vuelta al origen de objeto, que le permite escribir un visualizador que puede editar los datos. Invalidar el proveedor de objetos para comunicarse con el evaluador de expresiones y el origen del objeto.

El lado depurado y el lado depurador se comunican entre sí a través de <xref:System.IO.Stream> los métodos que serializan los datos de un objeto en un <xref:System.IO.Stream> y deserializar el <xref:System.IO.Stream> en un objeto de datos.

Puede escribir un visualizador para un tipo genérico solo si el tipo es un tipo abierto. Esta restricción es igual que la restricción de uso del atributo `DebuggerTypeProxy`. Para obtener más información, consulte [utilizar el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Los visualizadores personalizados pueden tener consideraciones de seguridad. Consulte [consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md).

Los pasos siguientes ofrecen una descripción general de creación de visualizador. Para obtener instrucciones detalladas, consulte [Tutorial: Escribir un visualizador en C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) o [Tutorial: Escribir un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Para crear el lado depurador

Para crear la interfaz de usuario del visualizador en el lado depurador, crea una clase que hereda de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>e invalidar la <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> método para mostrar la interfaz. Puede usar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar Windows forms, cuadros de diálogo y controles en el visualizador.

1. Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obtener el objeto visualizado en el lado depurador.

1. Cree una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Reemplace el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar su interfaz. Use <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> métodos para mostrar Windows forms, cuadros de diálogo y controles en la interfaz.

4. Aplicar <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador para mostrar (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>Para crear el lado depurado

Especificar el código del lado depurado mediante el <xref:System.Diagnostics.DebuggerVisualizerAttribute>.

1. Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, dándole un visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) y un origen de objeto (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Si se omite el origen del objeto, el visualizador utilizará un origen de objeto predeterminado.

1. Para permitir que el visualizador de editar, así como mostrar objetos de datos, reemplace el `TransferData` o `CreateReplacementObject` métodos desde <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

## <a name="see-also"></a>Vea también

- [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Tutorial: Escritura de un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Cómo: Instalación de un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Cómo: Prueba y depuración de un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Referencia de la API del visualizador](../debugger/visualizer-api-reference.md)
- [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
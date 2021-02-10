---
title: Creación de visualizadores de datos personalizados | Microsoft Docs
description: Los visualizadores del depurador de Visual Studio son componentes que muestran datos. Obtenga información sobre los seis visualizadores estándar y sobre cómo puede escribir o descargar otros.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f3d9a907d0857e918069fc4542d59d87242d609
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865844"
---
# <a name="create-custom-data-visualizers"></a>Creación de visualizadores de datos personalizados

 Un *visualizador* es un elemento de la interfaz de usuario del depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] que muestra una variable o un objeto de la manera adecuada para su tipo de datos. Por ejemplo, un visualizador HTML interpreta una cadena HTML y muestra el resultado tal como aparecería en una ventana del explorador. Un visualizador de mapa de bits interpreta una estructura de mapa de bits y muestra el gráfico que representa. Algunos visualizadores permiten modificar y ver los datos.

 El depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] incluye seis visualizadores estándar. Los visualizadores de texto, HTML, XML y JSON funcionan en objetos de cadena. El visualizador de árboles de WPF muestra las propiedades de un árbol visual de objetos de WPF. El visualizador de conjuntos de datos funciona para los objetos DataSet, DataView y DataTable.

Puede haber más visualizadores disponibles para su descarga de Microsoft, de terceros y de la comunidad. También puede escribir sus propios visualizadores e instalarlos en el depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

En el depurador, un visualizador se representa mediante un icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador"). Puede seleccionar el icono de una **información sobre datos**, la ventana **Inspección** o el cuadro de diálogo **Inspección rápida** del depurador y luego seleccionar el visualizador adecuado para el objeto correspondiente.

## <a name="write-custom-visualizers"></a>Creación de visualizadores personalizados

 > [!NOTE]
 > Para crear un visualizador personalizado para código nativo, vea el ejemplo del [visualizador del depurador nativo SQLite ](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer). Los visualizadores personalizados no son compatibles con aplicaciones de UWP y Windows 8.x.

Puede escribir un visualizador personalizado para un objeto de cualquier clase administrada, excepto <xref:System.Object> o <xref:System.Array>.

La arquitectura de un visualizador del depurador tiene dos partes:

- El *lado depurador* se ejecuta en el depurador de Visual Studio y crea y muestra la interfaz de usuario del visualizador.

- El *lado depurado* se ejecuta dentro del proceso que Visual Studio depura (el *depurado*). El objeto de datos que se va a visualizar (por ejemplo, un objeto String) existe en el proceso depurado. El lado depurado envía el objeto al lado depurador, que lo muestra en la interfaz de usuario que se crea.

El lado depurador recibe este objeto de datos que se visualizará desde un *proveedor de objetos* que implementa la interfaz <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>. El lado depurado envía el objeto a través del *origen de objeto*, que se deriva de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

El proveedor de objetos también puede devolver los datos al origen de objeto, lo que permite escribir un visualizador que puede editar datos. Reemplace el proveedor de objetos para comunicarse con el evaluador de expresiones y el origen de objeto.

El lado depurado y el lado depurador se comunican entre sí a través de métodos <xref:System.IO.Stream> que serializan un objeto de datos en <xref:System.IO.Stream> y deserializan de nuevo <xref:System.IO.Stream> en un objeto de datos.

Solo se puede escribir un visualizador para un tipo genérico si el tipo es abierto. Esta restricción es igual que la restricción de uso del atributo `DebuggerTypeProxy`. Para más información, vea [Uso del atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Los visualizadores personalizados pueden tener consideraciones de seguridad. Vea [Consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md).

En los pasos siguientes se ofrece información general de alto nivel sobre la creación de un visualizador. Para obtener instrucciones detalladas, vea [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) o [Tutorial: Escritura de un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Para crear el lado depurador

Para crear la interfaz de usuario del visualizador en el lado depurador, se crea una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> y se reemplaza el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar la interfaz. Puede utilizar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios, cuadros de diálogo y controles de Windows Forms en el visualizador.

1. Utilice los métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obtener el objeto visualizado en el lado depurador.

1. Cree una clase que herede de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Reemplace el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para mostrar su interfaz. Utilice métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para mostrar formularios, cuadros de diálogo y controles de Windows Forms en la interfaz.

4. Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute> asignándole el visualizador que se va a mostrar (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Para crear el origen del objeto de visualizador del lado depurado

En el código del depurador, edite el objeto <xref:System.Diagnostics.DebuggerVisualizerAttribute>, asignándole el tipo que se va a visualizar (el origen del objeto del lado depurado) (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). La propiedad `Target` establece el origen del objeto. Si omite el origen de objeto, se utilizará un origen de objeto predeterminado.

::: moniker range=">=vs-2019"
El código del lado depurado contiene el origen del objeto que se visualiza. El objeto de datos puede invalidar los métodos de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Un archivo DLL del lado depurado es necesario si desea crear un visualizador independiente.
::: moniker-end

En el código del lado depurado:

- Para permitir al visualizador editar objetos de datos, el origen de objetos debe heredar de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> e invalidar los métodos `TransferData` o `CreateReplacementObject`.

- Si necesita admitir la compatibilidad con múltiples versiones (multi-targeting) en el visualizador, puede usar los siguientes monikers de la plataforma de destino (TFM) en el archivo del proyecto del lado depurado.

   ```xml
   <TargetFrameworks>net20;netstandard2.0;netcoreapp2.0</TargetFrameworks>
   ```

   Estos son los únicos TFM admitidos.

## <a name="see-also"></a>Vea también

- [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Tutorial: Escritura de un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Cómo: Instalación de un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Cómo: Prueba y depuración de un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Referencia de la API del visualizador](../debugger/visualizer-api-reference.md)
- [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
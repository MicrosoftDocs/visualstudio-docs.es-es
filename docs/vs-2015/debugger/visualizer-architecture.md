---
title: Arquitectura del visualizador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ec6a27b8fcd35b4b74108f7bc608c975e120b02
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828694"
---
# <a name="visualizer-architecture"></a>Arquitectura de un visualizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La arquitectura de un visualizador del depurador tiene dos partes:  
  
- El *lado depurador* se ejecuta dentro del depurador de Visual Studio. El código del lado depurador crea y muestra la interfaz de usuario para el visualizador.  
  
- El *lado depurado* se ejecuta dentro del proceso de Visual Studio está depurando (el *depurado*).  
  
  Un visualizador es un componente del depurador que permite al depurador mostrar (*visualizar*) el contenido de un objeto de datos en un formato significativo y comprensible. Algunos visualizadores también admiten la edición del objeto de datos. Si escribe visualizadores personalizados, puede ampliar el depurador para que controle sus propios tipos de datos personalizados.  
  
  El objeto de datos que se pueden visualizar reside dentro del proceso que se está depurando (el *depurado* proceso). La interfaz de usuario que mostrará los datos se crea dentro del proceso del depurador de Visual Studio:  
  
|Proceso del depurador|Proceso depurado|  
|----------------------|----------------------|  
|Interfaz de usuario del depurador (Información sobre datos, ventana Inspección, Inspección rápida)|Objeto de datos que se va a visualizar|  
  
 Para visualizar el objeto de datos dentro de la interfaz del depurador, se necesita código para comunicarse entre los dos procesos. Por lo tanto, la arquitectura del visualizador consta de dos partes: *lado depurador* código y *lado depurado* código.  
  
 El código del lado del depurador crea su propia interfaz de usuario, a la que se puede invocar desde la interfaz del depurador, como una Información sobre datos, la ventana Inspección o Inspección rápida. La interfaz del visualizador se crea mediante la clase <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> y la interfaz <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>. Como todas las API del visualizador, DialogDebuggerVisualizer e IDialogVisualizerService se encuentran en el espacio de nombres <xref:Microsoft.VisualStudio.DebuggerVisualizers>.  
  
|Lado depurador|Lado depurado|  
|-------------------|-------------------|  
|Clase DialogDebuggerVisualizer<br /><br /> Interfaz IDialogVisualizerService|Objetos de datos|  
  
 La interfaz de usuario obtiene los datos que se van a visualizar de un proveedor de objetos, que se encuentra en el lado depurador:  
  
|Lado depurador|Lado depurado|  
|-------------------|-------------------|  
|Clase DialogDebuggerVisualizer<br /><br /> Interfaz IDialogVisualizerService|Objetos de datos|  
|Proveedor de objetos (implementa <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Hay un objeto correspondiente en el lado depurado denominado origen de objetos:  
  
|Lado depurador|Lado depurado|  
|-------------------|-------------------|  
|Clase DialogDebuggerVisualizer<br /><br /> Interfaz IDialogVisualizerService|Objetos de datos|  
|Proveedor de objetos (implementa <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Origen de objetos (se deriva de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 El proveedor de objetos proporciona los datos de objeto que van a visualizarse en la interfaz de usuario del visualizador. El proveedor de objetos recibe los datos de objeto del origen de objetos. El proveedor de objetos y el origen de objetos proporcionan una serie de API para que los datos de objeto se comuniquen entre el lado depurador y el lado depurado.  
  
 Cada visualizador debe obtener el objeto de datos que va a visualizarse. En la siguiente tabla se muestran las API correspondientes que el proveedor de objetos y el origen de objetos utilizan para este propósito:  
  
|Proveedor de objetos|Origen de objetos|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> -O bien-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Tenga en cuenta que el proveedor de objetos puede utilizar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> o <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Cada API genera una llamada a <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> en el origen de objetos. Una llamada a <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> rellena [System.IO.Stream] (<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->), que representa el formato serializado del objeto que se está visualizando.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> vuelve a deserializar los datos en el formato de objeto, que después se puede mostrar en la interfaz de usuario que se cree con <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> rellena los datos como <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> sin formato, que debe deserializar. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> funciona llamando a <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> para obtener los <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> serializados y deserializando los datos seguidamente. Utilice <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> cuando .NET no pueda serializar el objeto y se requiera una serialización personalizada. En tal caso, también deberá reemplazar el método <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>.  
  
 Si está creando un visualizador de sólo lectura, una comunicación unidireccional con <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> o <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> será suficiente. Si está creando un visualizador que admite la edición de objetos de datos, el proceso es más complicado. También debe poder enviar un objeto de datos desde el proveedor de objetos de vuelta al origen de objetos. En la siguiente tabla se muestran las API del proveedor de objetos y del origen de objetos que se utilizan para este fin:  
  
|Proveedor de objetos|Origen de objetos|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> -O bien-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 De nuevo, tenga en cuenta que hay dos API que el proveedor de objetos puede utilizar. Los datos siempre se envían desde el proveedor de objetos hasta el origen de objetos como <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, pero <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> requiere que serialice el objeto en <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> toma el objeto suministrado, lo serializa en <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> y, a continuación, llama a <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> para enviar <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> a <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 Al utilizar uno de los métodos de reemplazo, se crea un nuevo objeto de datos en el código depurado que reemplaza al objeto que está visualizándose. Si desea cambiar el contenido del objeto original sin reemplazarlo, utilice uno de los métodos de transferencia que se muestran en la siguiente tabla. Estas API transfieren los datos en ambas direcciones al mismo tiempo, sin reemplazar el objeto que se está visualizando:  
  
|Proveedor de objetos|Origen de objetos|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> -O bien-<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: escribir un visualizador](../debugger/how-to-write-a-visualizer.md)   
 [Tutorial: Escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Tutorial: Escribir un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Tutorial: Escribir un visualizador en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Consideraciones de seguridad del visualizador](../debugger/visualizer-security-considerations.md)




---
title: Comportamiento nuevo o cambiado con adaptadores de Editor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22028b1b2725f184c3d5748f2885a17d4bff0c60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148667"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamiento nuevo o cambiado con adaptadores de Editor
Si está actualizando el código escrito en versiones anteriores del editor principal de Visual Studio y tiene previsto usar el editor adaptadores (o correcciones de compatibilidad) en lugar de usar la nueva API, debe tener en cuenta las siguientes diferencias en el comportamiento de los adaptadores de editor en relación con el editor principal anterior.  
  
## <a name="features"></a>Características  
  
#### <a name="using-setsite"></a>Usar SetSite  
 Debe llamar a <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> cuando CoCreate búferes de texto, vistas de texto y ventanas de código antes de realizar ninguna otra operación en ellos. Sin embargo, esto no es necesario si utiliza la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> para crearlos, ya que llaman Create() métodos este servicio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Objeto IVsCodeWindow hospedaje y IVsTextView en su propio contenido  
 Puede hospedar ambos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en su propio contenido con el modo de Win32 o modo WPF. Sin embargo, debe tener en cuenta que hay algunas diferencias en los dos modos.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Usar las versiones de Win32 y WPF de objeto IVsCodeWindow  
 La ventana del editor de código se deriva de <xref:Microsoft.VisualStudio.Shell.WindowPane>, que implementa el anterior Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz, así como el nuevo WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaz. Puede usar el <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> método para crear un entorno de hospedaje basados en HWND, o la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> método para crear un entorno de hospedaje de WPF. El editor subyacente siempre utiliza WPF, pero puede crear el tipo de panel de ventana que se adapte a sus requisitos de hospedaje si va a incrustar este panel de la ventana directamente en su propio contenido.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Usar las versiones de Win32 y WPF de IVsTextView  
 Puede establecer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> al modo de Win32 o WPF.  
  
 Cuando un generador del editor crea una vista de texto, de forma predeterminada se hospeda en un HWND, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> devuelve un HWND. No debe utilizar este modo para incrustar el editor dentro de un control WPF.  
  
 Para establecer una vista de texto en modo WPF, debe llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> y pase <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> como uno de la inicialización de marca en el `InitView` parámetro. Puede obtener el <xref:System.Windows.FrameworkElement> mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Modo WPF difiere del modo de Win32 de dos maneras. En primer lugar, la vista de texto puede estar hospedada en un contexto WPF. Se puede obtener acceso al panel WPF convirtiendo el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> y llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Segundo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> todavía devuelve un HWND, pero este HWND puede usarse solo para comprobar su posición y establecer el foco en ella. No se debe usar esta HWND para responder a un mensaje WM_PAINT, porque no afectará a cómo el editor pinta la ventana. Este HWND está presente sólo para facilitar la transición al nuevo editor código por medio de los adaptadores. Se recomienda encarecidamente que no deben utilizar `VIF_NO_HWND_SUPPORT` si el componente requiere un HWND funcione, debido a las limitaciones en el HWND devuelto desde `GetWindowHandle` mientras se encuentre en este modo.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Pasar matrices como parámetros en código nativo  
 Existen muchos métodos en el editor heredado API que tienen parámetros que incluyen una matriz y su recuento. Algunos ejemplos son:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Si se llama a estos métodos en código nativo, debe pasar en un único elemento a la vez. Si se pasa más de un elemento, se rechazará la llamada, debido a problemas con la implementación de interoperabilidad primaria.  
  
 El problema es más complejo con métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Cada vez que se llama a este método, borra la lista anterior de tipos de marcador omitidos, por lo que no es posible simplemente llamar a este método tres veces con tres tipos de marcador diferente. La única solución es llamar a este método solo en código administrado.  
  
#### <a name="threading"></a>Subprocesos  
 El adaptador de búfer siempre se debe llamar desde el subproceso de interfaz de usuario. El adaptador de búfer es un objeto administrado, lo que significa que una llamada a él desde el código administrado pasará por alto la serialización de COM y la llamada no se realizará en el subproceso de interfaz de usuario.  Si el adaptador de búfer que está llamando desde un subproceso en segundo plano, debe utilizar <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un método similar.  
  
#### <a name="lockbuffer-methods"></a>Métodos de LockBuffer  
 Todos los métodos de LockBuffer() están en desuso. Algunos ejemplos son:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Confirmar eventos  
 Confirmar los eventos no se admiten. Llamar a un método que le informa de estos eventos hace que el método devuelva un código de error.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 El <xref:EnvDTE.TextEditorEvents> ya no se activan en Commit(). En su lugar, se activan en cada cambio de texto.  
  
#### <a name="text-markers"></a>Marcadores de texto  
 Debe llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objetos cuando se quita de ellos. En versiones anteriores, era necesario solo liberar los marcadores.  
  
#### <a name="line-numbers"></a>Números de línea  
 Para una amplia variedad de métodos en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, números de línea se corresponden con números de línea de búfer subyacente, los números de línea no ese valor en la esquematización y ajuste de palabras, como en Visual Studio 2008.  
  
 Los métodos que se ven afectados incluyen lo siguiente (la lista no es exhaustiva):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>esquematizar  
 Los clientes de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> verán sólo las regiones de esquematización que se agregaron con <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. No podrán ver regiones ad hoc, porque no se agregan a través de los adaptadores de editor. Del mismo modo, estos clientes no podrán ver agregadas por los lenguajes (incluidos C# y C++) que están usando el nuevo editor de código en lugar de los adaptadores de editor de regiones de esquematización.  
  
#### <a name="line-heights"></a>Alto de línea  
 En el editor de nuevo, las líneas de texto pueden tener distintas alturas, según el tamaño de fuente y las transformaciones de línea posibles que pueden mover la línea en relación con otras líneas. El alto de línea devuelto por métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> es el alto de una línea con el tamaño de fuente predeterminado sin transformaciones de línea aplicadas. Este alto puede o podría no reflejar el alto real de una línea en la vista.  
  
#### <a name="eventing-and-undo"></a>Eventos y deshacer  
 En el nuevo editor de la vista sigue realizar operaciones como la representación y generar eventos de forma continua, incluso cuando está abierto un clúster de deshacer. Este comportamiento es distinto de vistas heredadas, que no ha realizado esas operaciones hasta que después del cierre del clúster de deshacer.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> método se producirá un error si se pasa una clase que no implementan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Win32 personalizado ya no se admiten elementos emergentes dibujado por el propietario.  
  
#### <a name="smarttags"></a>Etiquetas inteligentes  
 No hay compatibilidad para las etiquetas inteligentes creadas con, adaptador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfaces.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> no está implementada.  
  
## <a name="unimplemented-methods"></a>Métodos no implementadas  
 Algunos métodos no han implementado en el adaptador de búfer de texto, el adaptador de vista de texto y el adaptador de la capa de texto.  
  
|Interfaz|No implementado|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` no está implementada.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> se implementa en los adaptadores pero se omite en la interfaz de usuario de esquematización.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> se implementa en los adaptadores pero se omite en la interfaz de usuario de esquematización.|
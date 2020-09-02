---
title: Comportamiento nuevo o cambiado con adaptadores de editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194177"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamiento nuevo o modificado con los adaptadores del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si está actualizando el código escrito en versiones anteriores del editor principal de Visual Studio y piensa usar los adaptadores del editor (o correcciones de compatibilidad) en lugar de usar la nueva API, debe tener en cuenta las siguientes diferencias en el comportamiento de los adaptadores del editor con respecto al editor principal anterior.  
  
## <a name="features"></a>Características  
  
#### <a name="using-setsite"></a>Usar SetSite ()  
 Debe llamar <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> al crear búferes de texto, vistas de texto y ventanas de código antes de realizar otras operaciones en ellos. Sin embargo, esto no es necesario si utiliza <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> para crearlos, ya que los propios métodos Create () de este servicio llaman a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hospedaje de IVsCodeWindow y IVsTextView en su propio contenido  
 Puede hospedar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en su propio contenido mediante el modo Win32 o el modo WPF. Sin embargo, debe tener en cuenta que hay algunas diferencias en los dos modos.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Usar las versiones Win32 y WPF de IVsCodeWindow  
 La ventana de código del editor se deriva de <xref:Microsoft.VisualStudio.Shell.WindowPane> , que implementa la interfaz Win32 más antigua, así <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> como la nueva <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaz WPF. Puede usar el <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> método para crear un entorno de hospedaje basado en HWND o el <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> método para crear un entorno de hospedaje de WPF. El editor subyacente siempre usa WPF, pero puede crear el tipo de panel de ventana que mejor se adapte a sus requisitos de hospedaje si va a incrustar este panel de ventana directamente en su propio contenido.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Usar las versiones Win32 y WPF de IVsTextView  
 Puede establecer en modo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 o en modo WPF.  
  
 Cuando un generador de editores crea una vista de texto, se hospeda de forma predeterminada dentro de un HWND y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> devuelve un HWND. No debe utilizar este modo para incrustar el editor dentro de un control de WPF.  
  
 Para establecer una vista de texto en modo WPF, debe llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> y pasar <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> como una de las marcas de inicialización en el `InitView` parámetro. Puede obtener llamando <xref:System.Windows.FrameworkElement> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 El modo WPF difiere del modo Win32 de dos maneras. En primer lugar, la vista de texto se puede hospedar en un contexto de WPF. Puede tener acceso al panel de WPF convirtiendo el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> y llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . En segundo lugar, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> todavía devuelve un HWND, pero este HWND solo se puede usar para comprobar su posición y establecer el foco en él. No debe usar este HWND para responder a un mensaje de WM_PAINT, ya que no afectará al modo en que el editor pinta la ventana. Este HWND solo está presente para facilitar la transición al nuevo código del editor por medio de los adaptadores. Se recomienda no usar `VIF_NO_HWND_SUPPORT` si el componente requiere que el elemento HWND funcione, debido a las limitaciones del HWND devuelto desde `GetWindowHandle` mientras se encuentra en este modo.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Pasar matrices como parámetros en código nativo  
 Hay muchos métodos en la API de editor heredada que tienen parámetros que incluyen una matriz y su recuento. Algunos ejemplos son:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Si llama a estos métodos en código nativo, debe pasar solo un elemento cada vez. Si se pasa más de un elemento, se rechazará la llamada debido a problemas con la implementación de la interoperabilidad primaria.  
  
 El problema es más complejo con métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Cada vez que se llama a este método, borra la lista anterior de tipos de marcador omitidos, por lo que no es posible llamar a este método tres veces con tres tipos de marcadores diferentes. La única solución es llamar a este método solo en código administrado.  
  
#### <a name="threading"></a>Subprocesos  
 Siempre debe llamar al adaptador de búfer desde el subproceso de la interfaz de usuario. El adaptador de búfer es un objeto administrado, lo que significa que, al llamar a él desde código administrado, se omitirá el cálculo de referencias COM y la llamada no se calculará automáticamente para el subproceso de interfaz de usuario.  Si llama al adaptador de búfer desde un subproceso en segundo plano, debe usar <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un método similar.  
  
#### <a name="lockbuffer-methods"></a>Métodos LockBuffer  
 Todos los métodos LockBuffer () están en desuso. Algunos ejemplos son:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Confirmar eventos  
 No se admiten los eventos de confirmación. La llamada a un método que aconseja para estos eventos hace que el método devuelva un código de error.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents>Ya no se activa en commit (). En su lugar, se activan en cada cambio de texto.  
  
#### <a name="text-markers"></a>Marcadores de texto  
 Debe llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objetos cuando los quite. En versiones anteriores, solo era necesario liberar los marcadores.  
  
#### <a name="line-numbers"></a>Números de línea  
 En el caso de una variedad de métodos en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> , los números de línea se corresponden con los números de línea del búfer subyacente, no con los números de línea que se incluyen en la esquematización y el ajuste automático de línea, como en Visual Studio 2008.  
  
 Entre los métodos afectados se incluyen los siguientes (la lista no es exhaustiva):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>esquematizar  
 Los clientes de verán <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> solo las regiones de esquematización que se agregaron mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . No verán regiones ad hoc, porque no se agregan a través de los adaptadores del editor. Del mismo modo, estos clientes no verán las regiones de esquematización agregadas por lenguajes (incluidos C# y C++) que usan el nuevo código del editor en lugar de los adaptadores del editor.  
  
#### <a name="line-heights"></a>Alto de línea  
 En el nuevo editor, las líneas de texto pueden tener distintos altos, en función del tamaño de fuente y las transformaciones de línea posibles que puedan trasladar la línea con respecto a otras líneas. El alto de línea devuelto por métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> es el alto de una línea usando el tamaño de fuente predeterminado sin aplicar transformaciones de línea. Este alto puede reflejar o no el alto real de una línea en la vista.  
  
#### <a name="eventing-and-undo"></a>Eventos y deshacer  
 En el nuevo editor, la vista continúa realizando operaciones como la representación y generación continua de eventos, incluso cuando un clúster para deshacer está abierto. Este comportamiento es diferente del de las vistas heredadas, que no realizaron esas operaciones hasta después del cierre del clúster de deshacer.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> método producirá un error si se pasa una clase que no implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Ya no se admiten los elementos emergentes dibujados por el propietario de Win32.  
  
#### <a name="smarttags"></a>Etiquetas inteligentes  
 No hay compatibilidad con el adaptador para las etiquetas inteligentes creadas con las <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> interfaces,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> no está implementado.  
  
## <a name="unimplemented-methods"></a>Métodos no implementados  
 Algunos métodos no se han implementado en el adaptador de búfer de texto, el adaptador de vista de texto y el adaptador de capa de texto.  
  
|Interfaz|No implementado|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` no está implementado.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> está implementado en los adaptadores, pero la interfaz de usuario de esquematización lo omite.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> está implementado en los adaptadores, pero la interfaz de usuario de esquematización lo omite.|

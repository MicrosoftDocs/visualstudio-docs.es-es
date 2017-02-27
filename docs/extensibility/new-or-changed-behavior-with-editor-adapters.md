---
title: "Comportamiento nuevo o cambiado con adaptadores de Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados: comportamiento del adaptador"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Comportamiento nuevo o cambiado con adaptadores de Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si está actualizando el código escrito en versiones anteriores del editor de Visual Studio core y tiene previsto usar el editor adaptadores \(o correcciones de compatibilidad\) en lugar de usar la nueva API, debe tener en cuenta las siguientes diferencias en el comportamiento de los adaptadores de editor con respecto a la anterior editor principal.  
  
## Características  
  
#### Usar SetSite  
 Se debe llamar a <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> cuando CoCreate búferes de texto, vistas de texto y código de windows antes de realizar otras operaciones en ellos. Sin embargo, esto no es necesario si utiliza el <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> para crearlas, debido a que Create\(\) métodos este servicio llaman <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### Objeto IVsCodeWindow hospedaje y IVsTextView en su propio contenido  
 Puede hospedar tanto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en su propio contenido utilizando el modo de Win32 o modo WPF. Sin embargo, debe tener en cuenta que existen algunas diferencias en los dos modos.  
  
##### Versiones de Win32 y WPF de objeto IVsCodeWindow  
 Se deriva de la ventana del editor de código <xref:Microsoft.VisualStudio.Shell.WindowPane>, que implementa el antiguo Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz, así como el nuevo WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaz. Puede usar el <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> para crear un entorno de hospedaje basadas en HWND, o la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> método para crear un entorno de hospedaje de WPF. El editor subyacente siempre usa WPF, pero puede crear el tipo de panel de ventana que se adapte a sus requisitos de hospedaje si va a incrustar este panel de ventana directamente en su propio contenido.  
  
##### Versiones de Win32 y WPF de IVsTextView  
 Puede establecer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> al modo de Win32 o WPF.  
  
 Cuando un generador del editor crea una vista de texto, de forma predeterminada, se hospeda en un HWND y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> devuelve un HWND. No debe utilizar este modo para incrustar el editor dentro de un control WPF.  
  
 Para definir una vista de texto a modo WPF, debe llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> y pase <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> como uno de la inicialización de marcas en el `InitView` parámetro. Puede obtener el <xref:System.Windows.FrameworkElement> llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Modo WPF difiere del modo de Win32 de dos maneras. En primer lugar, la vista de texto puede estar hospedada en un contexto WPF. Se puede obtener acceso al panel WPF convirtiendo el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> y llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Segundo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> todavía devuelve un HWND, pero este HWND puede usarse sólo para comprobar su posición y establecer el foco en ella. No debe utilizar este HWND para responder a un mensaje WM\_PAINT, porque no afectará a cómo dibuja el editor de la ventana. HWND está presente sólo para facilitar la transición hacia el nuevo editor de código mediante los adaptadores. Se recomienda encarecidamente que no debe utilizar `VIF_NO_HWND_SUPPORT` Si el componente requiere un HWND funcione, debido a las limitaciones en HWND devuelto desde `GetWindowHandle` mientras está en este modo.  
  
#### Pasar matrices como parámetros en el código nativo  
 Hay muchos métodos en el editor de API heredado que tienen parámetros que incluyen una matriz y su recuento. Algunos ejemplos son:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Si se llama a estos métodos en código nativo, debe pasar en un solo elemento a la vez. Si se pasa más de un elemento, se rechazará la llamada, debido a problemas con la implementación de interoperabilidad principal.  
  
 El problema es más complejo con métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Cada vez que se llama a este método, se borra la lista anterior de tipos de marcador omitidos, por lo que no es posible simplemente llamar a este método tres veces con tres tipos diferentes de marcador. La única solución es llamar a este método en el código administrado.  
  
#### Subprocesamiento  
 Adaptador de búfer siempre se debe llamar desde el subproceso de interfaz de usuario. El adaptador de búfer es un objeto administrado, lo que significa que la llamada a él desde el código administrado omitirá el cálculo de referencias COM y la llamada no se realizará al subproceso de interfaz de usuario.  Si el adaptador de búfer que está llamando desde un subproceso en segundo plano, debe utilizar <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un método similar.  
  
#### Métodos LockBuffer  
 Todos los métodos de LockBuffer\(\) están obsoletos. Algunos ejemplos son:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### Confirmar eventos  
 Confirmar eventos no son compatibles. Llamar a un método que le informa de estos eventos hace que el método devuelva un código de error.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 El <xref:EnvDTE.TextEditorEvents> ya no se activan en Commit\(\). En su lugar, se activan en cada cambio de texto.  
  
#### Marcadores de texto  
 Se debe llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objetos cuando se quita de ellos. En versiones anteriores, era necesario solo liberar los marcadores.  
  
#### Números de línea  
 Para una variedad de métodos en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, los números de línea se corresponden con los números de línea de búfer subyacente, los números de línea no que factor de esquematización y ajuste en Visual Studio 2008.  
  
 Los métodos afectados incluyen lo siguiente \(la lista no es exhaustiva\):  
  
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
  
#### Esquematización  
 Los clientes de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> verá solo las regiones de esquematización que se agregaron con <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. No verá regiones ad hoc, ya que no se agregan a través de los adaptadores de editor. Asimismo, estos clientes no verán agregadas idiomas \(incluidos C\# y C\+\+\) que utilizan el nuevo editor de código en lugar de los adaptadores de editor de regiones de esquematización.  
  
#### Alto de línea  
 En el nuevo editor de líneas de texto pueden tener distintas alturas, según el tamaño de fuente y transformaciones de línea posibles que pueden mover la línea en relación con otras líneas. El alto de línea devuelto por métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> es el alto de una línea con el tamaño de fuente predeterminado sin transformaciones de línea aplicadas. Este alto puede o no reflejen el alto de una línea en la vista.  
  
#### Eventos y deshacer  
 En el nuevo editor de la vista sigue realizar operaciones como la representación y provocar eventos continuamente, incluso cuando está abierto un clúster de deshacer. Este comportamiento es diferente de vistas heredadas, que no se ha realizado estas operaciones hasta después del cierre del clúster de deshacer.  
  
#### IntelliSense  
  
-   El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> método generará un error si se pasa una clase que no implementan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Win32 personalizado ya no se admiten elementos emergentes dibujado por el propietario.  
  
#### Etiquetas inteligentes  
 No hay compatibilidad con etiquetas inteligentes creadas con, adaptador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfaces.  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> no está implementado.  
  
## Métodos implementados  
 Algunos métodos no se han implementado en el adaptador de búfer de texto, el adaptador de vista de texto y el adaptador de la capa de texto.  
  
|Interfaz|No implementado|  
|--------------|---------------------|  
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
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> se implementa en los adaptadores, pero se omite en la interfaz de usuario de esquematización.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> se implementa en los adaptadores, pero se omite en la interfaz de usuario de esquematización.|
---
title: "Documento carga retrasada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Documento carga retrasada
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se carga inmediatamente. El marco de la ventana de documento se crea en un estado de espera de inicialización y un documento de marcador de posición \(llamado un marco de código auxiliar\) se coloca en la tabla de documento ejecutando \(RDT\).  
  
 La extensión puede producir documentos del proyecto cargarán innecesariamente mediante una consulta de elementos de los documentos antes de cargarse. Esto puede aumentar el espacio de memoria general para Visual Studio.  
  
## Carga de documento  
 El marco de código auxiliar y el documento completo se inicializan cuando el usuario tiene acceso al documento, por ejemplo, seleccione la ficha del marco de ventana. El documento también se puede inicializar una extensión que solicita los datos del documento, obtener acceso a lo RDT directamente para adquirir los datos del documento o acceso indirectamente a lo RDT realizando una de las siguientes llamadas:  
  
-   El marco de ventana método show: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   El marco de ventana GetProperty \(método\) <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> en cualquiera de las siguientes propiedades:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Si la extensión usa código administrado, no debería llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que esté seguro de que el documento no está en el estado de espera de inicialización o desea que el documento que se inicialice... Esto es debido a que este método siempre devuelve el documento objeto de datos, creándola si es necesario. En su lugar, debe llamar a uno de los métodos en la interfaz IVsRunningDocumentTable4.  
  
 Si la extensión utiliza C\+\+, puede pasar `null` para los parámetros que no desee.  
  
 Puede evitar la carga de documento innecesarios llamando a uno de los métodos siguientes antes de solicitar las propiedades pertinentes: antes de solicitar otras propiedades.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> mediante <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método devuelve un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que incluye un valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Si el documento aún no se ha inicializado.  
  
 Puede averiguar si se ha cargado un documento suscribiéndose al evento RDT que se desencadena cuando un documento está totalmente inicializado. Existen dos posibilidades:  
  
-   Si el receptor de eventos implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   De lo contrario, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 El siguiente es un escenario de acceso del documento hipotético. Un extensión desea mostrar información acerca de los documentos abiertos en Visual Studio, por ejemplo la edición bloquear recuento y algo acerca de los datos del documento. Enumera los documentos en el RDT mediante <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, a continuación, llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento con el fin de recuperar los datos de documentos de recuento del bloqueo edición. Si el documento está en el estado de espera de inicialización, solicita los datos del documento hace que se inicialice innecesariamente.  
  
 Una manera más eficaz de hacerlo es usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obtener el recuento de bloqueos de edición y, a continuación, utilice <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar si se ha inicializado el documento. Si no se incluyen las marcas de <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, el documento ya se ha inicializado y solicitar los datos del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> no hace que las inicializaciones innecesarias. Si se incluyen las marcas de <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, la extensión se deben solicitar los datos del documento hasta que se inicialice el documento. Esto se puede detectar en el controlador de eventos OnAfterAttributeChange\(Ex\).  
  
## Comprobar las extensiones para ver si forzar la inicialización  
 No hay ninguna indicación visible para indicar si se ha inicializado un documento, lo que puede ser difícil averiguar si la extensión está forzando la inicialización. Puede establecer una clave del registro que facilita la comprobación porque hace que el título de cada documento que no está completamente inicializado para que el texto `[Stub]` en el título.  
  
 En **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, establezca **StubTabTitleFormatString** a **{0} \[código auxiliar\]**.
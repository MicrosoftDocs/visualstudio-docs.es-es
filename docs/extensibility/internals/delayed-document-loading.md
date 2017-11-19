---
title: Documento carga retrasada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 794eccaf59b65044840d459bbde2e17eab8684a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="delayed-document-loading"></a>Documento carga retrasada
Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se carga de forma inmediata. El marco de la ventana de documento se crea en un estado pendiente de inicialización y un documento de marcador de posición (llamado un marco de código auxiliar) se coloca en la tabla de documento ejecutando (RDT).  
  
 La extensión puede producir documentos del proyecto que va a cargar innecesariamente mediante una consulta de elementos de los documentos antes de cargarse. Esto puede aumentar el consumo de memoria global para Visual Studio.  
  
## <a name="document-loading"></a>Carga de documento  
 El marco de código auxiliar y el documento se inicializan totalmente cuando el usuario tiene acceso al documento, por ejemplo, seleccione la pestaña del marco de ventana. El documento también se pueden inicializar con una extensión que solicita los datos del documento, obtiene acceso a la RDT directamente con el fin de adquirir los datos del documento o tener acceso a la RDT indirectamente mediante la realización de una de las llamadas siguientes:  
  
-   El marco de ventana show (método): <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   El marco de ventana GetProperty (método) <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> en cualquiera de las siguientes propiedades:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Si la extensión usa código administrado, no debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que esté seguro de que el documento no está en el estado pendiente de inicialización, o desea que el documento esté totalmente inicializada... Esto es debido a que este método siempre devuelve documentos objeto de datos, creándola si es necesario. En su lugar, debe llamar a uno de los métodos en la interfaz IVsRunningDocumentTable4.  
  
 Si la extensión utiliza C++, puede pasar `null` para los parámetros que no desee.  
  
 Puede evitar la carga de documento innecesarios llamando a uno de los métodos siguientes antes de solicitar las propiedades pertinentes: antes de solicitar otras propiedades.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>mediante <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método devuelve un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que incluye un valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> si aún no se ha inicializado el documento.  
  
 Puede averiguar cuándo se ha cargado un documento si se suscribe al evento RDT que se desencadena cuando un documento está totalmente inicializado. Hay dos posibilidades:  
  
-   Si el receptor de eventos implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   En caso contrario, es posible suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 El siguiente es un escenario de acceso de documento hipotético. Un extensión desea mostrar información acerca de los documentos abiertos en Visual Studio, por ejemplo la edición bloquear recuento y algo acerca de los datos del documento. Enumera los documentos en el RDT mediante <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, a continuación, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento con el fin de recuperar los datos de recuento y documento de bloqueo de edición. Si el documento está en el estado pendiente de inicialización, que solicita los datos del documento hace que se inicialice innecesariamente.  
  
 Una manera más eficaz de hacerlo es usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obtener el recuento de bloqueos de editar y, a continuación, utilice <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar si se ha inicializado el documento. Si no incluye las marcas de <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, el documento ya se ha inicializado y solicitar los datos del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> no produzca cualquier inicialización innecesario. Si incluye las marcas de <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, la extensión se deben solicitar los datos del documento hasta que se inicialice el documento. Esto se puede detectar en el controlador de eventos OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Comprobar las extensiones para ver si hacen que la inicialización  
 No hay ninguna indicación visible para indicar si se ha inicializado un documento, por lo que puede ser difícil averiguar si la extensión está forzando la inicialización. Puede establecer una clave del registro que facilita la comprobación, porque hace que el título de cada documento que no está totalmente inicializado para que tenga el texto `[Stub]` en el título.  
  
 En **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, establezca **StubTabTitleFormatString** a **{0} [código auxiliar]**.
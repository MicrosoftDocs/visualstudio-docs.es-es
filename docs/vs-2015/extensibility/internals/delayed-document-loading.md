---
title: Carga de documentos retrasada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196868"
---
# <a name="delayed-document-loading"></a>Carga de documentos retrasada
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se carga inmediatamente. El marco de ventana de documento se crea en un estado de espera de inicialización y un documento de marcador de posición (llamado un marco de código auxiliar) se coloca en la tabla de documentos en ejecución (RDT).  
  
 La extensión puede hacer que los documentos del proyecto que va a cargar innecesariamente consultando elementos de los documentos antes de cargarse. Esto puede aumentar el consumo de memoria general para Visual Studio.  
  
## <a name="document-loading"></a>Carga de documentos  
 El marco de código auxiliar y el documento se inicializan totalmente cuando el usuario tiene acceso al documento, por ejemplo, seleccione la pestaña del marco de ventana. También se puede inicializar el documento por una extensión que solicita los datos del documento, obtener acceso a la RDT directamente para adquirir los datos del documento, o tener acceso a la RDT indirectamente mediante la realización de una de las siguientes llamadas:  
  
- El marco de ventana método show: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
- El marco de ventana método GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> en cualquiera de las siguientes propiedades:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Si su extensión usa código administrado, no debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que esté seguro de que el documento no está en el estado de espera de inicialización o desea que el documento esté totalmente inicializada... Esto es porque este método siempre devuelve el documento de objeto de datos, crearla si fuera necesario. En su lugar, debe llamar a uno de los métodos en la interfaz IVsRunningDocumentTable4.  
  
  Si la extensión usa C++, puede pasar `null` para los parámetros que no desee.  
  
  Puede evitar la carga innecesaria documento llamando a uno de los métodos siguientes antes de solicitar las propiedades pertinentes: antes de solicitar otras propiedades.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> uso de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> Este método devuelve un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que incluye un valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> si aún no se ha inicializado el documento.  
  
  Puede averiguar cuándo se ha cargado un documento suscribiéndose a los eventos RDT que se desencadena cuando un documento está completamente inicializado. Existen dos posibilidades:  
  
- Si implementa el receptor de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- En caso contrario, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
  El siguiente es un escenario de acceso de documento hipotético. Visual Studio extensión desea mostrar información sobre los documentos abiertos, por ejemplo la edición de bloqueo recuento y algo acerca de los datos del documento. Enumera los documentos en el RDT utilizando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, a continuación, llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento con el fin de recuperar los datos de recuento y el documento de bloqueo de edición. Si el documento está en el estado de espera de inicialización, que solicita los datos del documento hace que se puede inicializar innecesariamente.  
  
  Una forma más eficaz de hacerlo es usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obtener el recuento de bloqueos de edición y, a continuación, usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar si se ha inicializado el documento. Si no se incluyen las marcas de <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, el documento ya se ha inicializado y solicitar los datos del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> no provoca ninguna inicialización innecesario. Si las marcas incluyen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, debe evitar la extensión que solicita los datos del documento hasta que se inicializa el documento. Esto se puede detectar en el controlador de eventos OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Extensiones para ver si forzar la inicialización de pruebas  
 No hay ninguna indicación visible para indicar si se ha inicializado un documento, por lo que puede ser difícil de averiguar si la extensión está forzando la inicialización. Puede establecer una clave del registro que facilita la comprobación, porque hace que el título de cada documento que no está completamente inicializado para que el texto `[Stub]` en el título.  
  
 En **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]** , establezca **StubTabTitleFormatString** a  **{0} [código auxiliar]** .

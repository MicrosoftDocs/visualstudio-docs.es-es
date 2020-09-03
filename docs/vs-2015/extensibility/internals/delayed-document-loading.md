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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196868"
---
# <a name="delayed-document-loading"></a>Carga de documentos retrasada
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se cargan inmediatamente. El marco de la ventana de documento se crea en un estado de inicialización pendiente y un documento de marcador de posición (denominado marco de código auxiliar) se coloca en la tabla de documentos en ejecución (RDT).  
  
 La extensión puede hacer que los documentos de proyecto se carguen innecesariamente consultando los elementos de los documentos antes de cargarlos. Esto puede aumentar la superficie de memoria total de Visual Studio.  
  
## <a name="document-loading"></a>Carga de documentos  
 El marco y el documento de código auxiliar se inicializan por completo cuando el usuario tiene acceso al documento, por ejemplo, seleccionando la pestaña del marco de la ventana. También se puede inicializar el documento mediante una extensión que solicita los datos del documento, ya sea mediante el acceso directo a RDT para adquirir los datos del documento o el acceso directo a RDT mediante una de las siguientes llamadas:  
  
- El método Show del marco de la ventana: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- El método GetProperty del marco de ventana <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> en cualquiera de las siguientes propiedades:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Si la extensión usa código administrado, no debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a a menos que esté seguro de que el documento no está en el estado de inicialización pendiente o desea que el documento se inicialice completamente. Esto se debe a que este método siempre devuelve el objeto de datos de documento y lo crea si es necesario. En su lugar, debe llamar a uno de los métodos de la interfaz IVsRunningDocumentTable4.  
  
  Si la extensión usa C++, puede pasar `null` para los parámetros que no desea.  
  
  Puede evitar la carga de documentos innecesaria mediante una llamada a uno de los métodos siguientes antes de solicitar las propiedades pertinentes: antes de solicitar otras propiedades.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utilizando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método devuelve un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que incluye un valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> si el documento aún no se ha inicializado.  
  
  Para averiguar cuándo se ha cargado un documento, suscríbase al evento RDT que se genera cuando un documento se inicializa por completo. Hay dos posibilidades:  
  
- Si el receptor de eventos implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- De lo contrario, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  El siguiente es un escenario hipotético de acceso a documentos. Una extensión de Visual Studio desea mostrar información sobre los documentos abiertos, por ejemplo, el recuento de bloqueos de edición y algo sobre los datos del documento. Enumera los documentos de RDT mediante <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> y, a continuación, llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento para recuperar el número de bloqueos de edición y los datos del documento. Si el documento se encuentra en el estado de inicialización pendiente, al solicitar los datos del documento, se inicializa innecesariamente.  
  
  Una manera más eficaz de hacerlo es usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obtener el número de bloqueos de edición y, a continuación, utilizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar si el documento se ha inicializado. Si las marcas no incluyen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , el documento ya se ha inicializado y al solicitar los datos del documento con, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> no se produce ninguna inicialización innecesaria. Si las marcas incluyen <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , la extensión debe evitar solicitar los datos del documento hasta que se inicialice el documento. Esto puede detectarse en el controlador de eventos OnAfterAttributeChange (ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Probar las extensiones para ver si fuerza la inicialización  
 No hay ninguna indicación visible para indicar si se ha inicializado un documento, por lo que puede ser difícil averiguar si la extensión está forzando la inicialización. Puede establecer una clave del registro que facilite la comprobación, ya que hace que el título de todos los documentos que no se inicializan completamente tenga el texto `[Stub]` en el título.  
  
 En **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]**, establezca **StubTabTitleFormatString** en ** {0} [stub]**.

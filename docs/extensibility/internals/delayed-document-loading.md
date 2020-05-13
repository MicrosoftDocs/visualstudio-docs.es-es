---
title: Carga de documentos retrasadas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708813"
---
# <a name="delayed-document-loading"></a>Carga de documentos retrasada

Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se cargan inmediatamente. El marco de la ventana del documento se crea en un estado de inicialización pendiente y un documento de marcador de posición (denominado marco de código auxiliar) se coloca en la tabla Documento en ejecución (RDT).

La extensión puede hacer que los documentos del proyecto se carguen innecesariamente consultando elementos de los documentos antes de que se carguen, lo que puede aumentar el espacio de memoria general de Visual Studio.

## <a name="document-loading"></a>Carga de documentos

El marco de código auxiliar y el documento se inicializan completamente cuando el usuario accede al documento, por ejemplo, seleccionando la pestaña del marco de ventana. El documento también se puede inicializar mediante una extensión que solicita los datos del documento, ya sea accediendo al RDT directamente para adquirir los datos del documento o accediendo al RDT indirectamente realizando una de las siguientes llamadas:

- El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> de marco de ventana.

- El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> de marco de ventana en cualquiera de las siguientes propiedades:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Si la extensión utiliza código administrado, no debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que esté seguro de que el documento no está en el estado de inicialización pendiente o desea que el documento se inicialice completamente. La razón es porque el método siempre devuelve el objeto de datos doc, creándolo si es necesario. En su lugar, debe llamar `IVsRunningDocumentTable4` a uno de los métodos en la interfaz.

- Si la extensión utiliza C++, puede pasar `null` los parámetros que no desea.

- Puede evitar la carga innecesaria de documentos llamando a uno de los métodos siguientes antes de solicitar las propiedades relevantes antes de solicitar otras propiedades:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>usando [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> devuelve un objeto que incluye un valor para [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) si el documento aún no se ha inicializado.

Puede averiguar cuándo se ha cargado un documento suscribiéndose al evento RDT que se genera cuando un documento se inicializa por completo. Hay dos posibilidades:

- Si el receptor <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>de eventos se <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>implementa, puede suscribirse a ,

- De lo contrario, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>puede suscribirse a .

El ejemplo siguiente es un escenario de acceso a documentos hipotético: una extensión de Visual Studio desea mostrar información sobre documentos abiertos, por ejemplo, el recuento de bloqueos de edición y algo sobre los datos del documento. Enumera los documentos en el <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>RDT <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> mediante , a continuación, llama a cada documento con el fin de recuperar el recuento de bloqueo de edición y los datos del documento. Si el documento está en estado de inicialización pendiente, solicitar los datos del documento hace que se inicialice innecesariamente.

Una forma más eficaz de obtener <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> acceso a un documento es <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> usar para obtener el recuento de bloqueos de edición y, a continuación, usar para determinar si el documento se ha inicializado. Si las marcas no incluyen [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), el documento ya se ha inicializado <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> y solicitar los datos del documento con no provoca ninguna inicialización innecesaria. Si las marcas incluyen [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), la extensión debe evitar solicitar los datos del documento hasta que se inicialice el documento. Esta inicialización se `OnAfterAttributeChange(Ex)` puede detectar en el controlador de eventos.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Probar extensiones para ver si fuerzan la inicialización

No hay ninguna indicación visible para indicar si se ha inicializado un documento, por lo que puede ser difícil averiguar si la extensión está forzando la inicialización. Puede establecer una clave del Registro que facilite la verificación, ya que hace que el título de cada documento que no está completamente inicializado tenga el texto *[Stub]* en el título.

En **HKEY_CURRENT_USER, Software, Microsoft, VisualStudio, 14,0, BackgroundSolutionLoad**, establezca **StubTabTitleFormatString** en * {0} [Stub]*.

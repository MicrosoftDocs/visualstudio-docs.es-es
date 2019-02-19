---
title: Carga de documentos retrasada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a3520b2bf1d6111e945f037502a589feed0d80a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335329"
---
# <a name="delayed-document-loading"></a>Carga de documentos retrasada

Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se carga inmediatamente. El marco de ventana de documento se crea en un estado de espera de inicialización y se coloca un documento de marcador de posición (llamado un marco de código auxiliar) en la tabla de documentos de ejecución (RDT).

La extensión puede hacer que los documentos del proyecto que va a cargar innecesariamente consultando elementos de los documentos antes de cargar, lo que pueden aumentar el consumo de memoria general para Visual Studio.

## <a name="document-loading"></a>Carga de documentos

El marco de código auxiliar y el documento se inicializan totalmente cuando el usuario tiene acceso al documento, por ejemplo, seleccione la pestaña del marco de ventana. También se puede inicializar el documento por una extensión que solicita los datos del documento, obtener acceso a la RDT directamente para adquirir los datos del documento, o tener acceso a la RDT indirectamente mediante la realización de una de las siguientes llamadas:

- El marco de ventana <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método.

- El marco de ventana <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método en cualquiera de las siguientes propiedades:

   - [__VSFPROPID.VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

   - [__VSFPROPID.VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

   - [__VSFPROPID.VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

   - [__VSFPROPID.VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

   - [__VSFPROPID.VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

   - [__VSFPROPID.VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Si su extensión usa código administrado, no debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que esté seguro de que el documento no está en el estado de espera de inicialización o desea que el documento esté totalmente inicializada. La razón es que el método siempre devuelve el documento de objeto de datos, crearla si fuera necesario. En su lugar, se debe llamar a uno de los métodos en el `IVsRunningDocumentTable4` interfaz.

- Si la extensión usa C++, puede pasar `null` para los parámetros que no desee.

- No puede cargar llamando a uno de los métodos siguientes antes de solicitar las propiedades pertinentes antes de solicitar otras propiedades de documento innecesaria:

   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> uso de [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método devuelve un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que incluye un valor para [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) si aún no se ha inicializado el documento.

Puede averiguar cuándo se ha cargado un documento suscribiéndose a los eventos RDT que se desencadena cuando un documento está completamente inicializado. Existen dos posibilidades:

- Si implementa el receptor de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,

- En caso contrario, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.

El ejemplo siguiente es un escenario de acceso de documento hipotético: Visual Studio de extensión desea mostrar información sobre los documentos abiertos, por ejemplo la edición de bloqueo recuento y algo acerca de los datos del documento. Enumera los documentos en el RDT utilizando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, a continuación, llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento con el fin de recuperar los datos de recuento y el documento de bloqueo de edición. Si el documento está en el estado de espera de inicialización, que solicita los datos del documento hace que se puede inicializar innecesariamente.

Una forma más eficaz de obtener acceso a un documento es usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obtener el recuento de bloqueos de edición y, a continuación, usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar si se ha inicializado el documento. Si no se incluyen las marcas de [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), el documento ya se ha inicializado y solicitar los datos del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> no provoca ninguna inicialización innecesario. Si las marcas incluyen [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), debe evitar la extensión que solicita los datos del documento hasta que se inicializa el documento. Esta inicialización se puede detectar en el `OnAfterAttributeChange(Ex)` controlador de eventos.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Extensiones para ver si forzar la inicialización de prueba

No hay ninguna indicación visible para indicar si se ha inicializado un documento, por lo que puede ser difícil de averiguar si la extensión está forzando la inicialización. Puede establecer una clave del registro que facilita la comprobación, porque hace que el título de cada documento que no está completamente inicializado para que el texto *[código auxiliar]* en el título.

En **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, establezca **StubTabTitleFormatString** a  *{0} [código auxiliar]*.
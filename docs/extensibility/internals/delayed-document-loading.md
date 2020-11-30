---
title: Carga de documentos retrasada | Microsoft Docs
description: Obtenga información sobre la carga diferida de documentos en Visual Studio y cómo codificar las extensiones para que no consulten los elementos de un documento antes de cargarlos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6489c819efe0fd29cd2d120c08414cf0532ad6f
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328397"
---
# <a name="delayed-document-loading"></a>Carga de documentos retrasada

Cuando un usuario vuelve a abrir una solución de Visual Studio, la mayoría de los documentos asociados no se cargan inmediatamente. El marco de la ventana de documento se crea en un estado de inicialización pendiente y un documento de marcador de posición (denominado marco de código auxiliar) se coloca en la tabla de documentos en ejecución (RDT).

La extensión puede hacer que los documentos de proyecto se carguen innecesariamente consultando los elementos de los documentos antes de cargarse, lo que puede aumentar la superficie de memoria total de Visual Studio.

## <a name="document-loading"></a>Carga de documentos

El marco y el documento de código auxiliar se inicializan por completo cuando el usuario tiene acceso al documento, por ejemplo, seleccionando la pestaña del marco de la ventana. También se puede inicializar el documento mediante una extensión que solicita los datos del documento, ya sea mediante el acceso directo a RDT para adquirir los datos del documento o el acceso directo a RDT mediante una de las siguientes llamadas:

- Método de marco de la ventana <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .

- El método de marco <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> de ventana en cualquiera de las siguientes propiedades:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Si la extensión usa código administrado, no debe llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a a menos que esté seguro de que el documento no está en el estado de inicialización pendiente o desea que el documento se inicialice completamente. La razón es que el método siempre devuelve el objeto de datos de documento y lo crea si es necesario. En su lugar, debe llamar a uno de los métodos de la `IVsRunningDocumentTable4` interfaz.

- Si la extensión usa C++, puede pasar `null` para los parámetros que no desea.

- Puede evitar la carga de documentos innecesaria mediante una llamada a uno de los métodos siguientes antes de solicitar las propiedades pertinentes antes de solicitar otras propiedades:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> uso de [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método devuelve un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que incluye un valor para [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) si el documento aún no se ha inicializado.

Para averiguar cuándo se ha cargado un documento, suscríbase al evento RDT que se genera cuando un documento se inicializa por completo. Hay dos posibilidades:

- Si el receptor de eventos implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- De lo contrario, puede suscribirse a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

El ejemplo siguiente es un escenario hipotético de acceso a documentos: una extensión de Visual Studio desea mostrar información sobre los documentos abiertos, por ejemplo, el recuento de bloqueos de edición y algo sobre los datos del documento. Enumera los documentos de RDT mediante <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> y, a continuación, llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento para recuperar el número de bloqueos de edición y los datos del documento. Si el documento se encuentra en el estado de inicialización pendiente, al solicitar los datos del documento, se inicializa innecesariamente.

Una manera más eficaz de obtener acceso a un documento es usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obtener el número de bloqueos de edición y, a continuación, utilizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar si el documento se ha inicializado. Si las marcas no incluyen [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), el documento ya se ha inicializado y al solicitar los datos del documento con, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> no se produce ninguna inicialización innecesaria. Si los marcadores incluyen [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), la extensión debe evitar solicitar los datos del documento hasta que se inicialice el documento. Esta inicialización se puede detectar en el `OnAfterAttributeChange(Ex)` controlador de eventos.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Extensiones de prueba para ver si fuerza la inicialización

No hay ninguna indicación visible para indicar si se ha inicializado un documento, por lo que puede ser difícil averiguar si la extensión está forzando la inicialización. Puede establecer una clave del registro que facilite la comprobación, ya que hace que el título de todos los documentos que no se inicializan completamente tenga el texto *[stub]* en el título.

En **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, establezca **StubTabTitleFormatString** en *{0} [stub]*.

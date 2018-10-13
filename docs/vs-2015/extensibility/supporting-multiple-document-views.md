---
title: Compatibilidad con varias vistas de documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c82100a544a9f59fbb64af8b78d51314b39690f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282706"
---
# <a name="supporting-multiple-document-views"></a>Compatibilidad con vistas de varios documentos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede proporcionar más de una vista de un documento mediante la creación de datos de documento independiente y objetos de vista de documento para el editor. Algunos casos en que una vista de documento adicionales sería útil son:  
  
-   Nueva compatibilidad con las ventanas: desea que el editor para proporcionar dos o más vistas del mismo tipo, para que un usuario que ya tiene una ventana abierta en el editor puede abrir una ventana nueva seleccionando el **nueva ventana** comando desde el **ventana** menú.  
  
-   Formulario y el código ver soporte técnico: desea que el editor para proporcionar vistas de tipos diferentes. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], por ejemplo, proporciona una vista de formulario y una vista de código.  
  
 Para obtener más información al respecto, consulte el procedimiento CreateEditorInstance en el archivo EditorFactory.cs en el proyecto de editor personalizado creado por la plantilla de paquete de Visual Studio. Para obtener más información sobre este proyecto, vea [Tutorial: crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Sincronizando las vistas  
 Al implementar varias vistas, el objeto de datos es responsable de mantener sincronizadas con los datos de todas las vistas. Puede usar en las interfaces de control de eventos <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para sincronizar varias vistas con los datos.  
  
 Si no usa el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto para sincronizar varias vistas, a continuación, debe implementar su propio sistema de eventos para controlar los cambios realizados en el objeto de datos. Puede usar distintos niveles de granularidad para mantener actualizado varias vistas. Con un valor de la máxima granularidad, a medida que escribe en una vista de las otras vistas se actualizan inmediatamente. Con una granularidad mínima, otras vistas no se actualizan hasta que se activan.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Determinar los datos del documento si está ya abierto  
 La tabla de documentos en ejecución (RDT) en el entorno de desarrollo integrado (IDE) le ayuda a realizar un seguimiento de si los datos de un documento ya están abiertos, como se muestra en el diagrama siguiente.  
  
 ![Gráfico de DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Varias vistas  
  
 De forma predeterminada, cada vista (objeto de vista de documento) está incluida en su propio marco de ventana (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Como ya hemos visto, sin embargo, los datos de documento pueden mostrarse en varias vistas. Para habilitar esta opción, Visual Studio comprueba la RDT para determinar si el documento en cuestión ya está abierto en un editor. Cuando se llama el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear el editor, se devuelve un valor distinto de NULL en la `punkDocDataExisting` parámetro indica que el documento ya está abierto en otro editor. Para obtener más información acerca de cómo ver las funciones RDT [tabla de documentos en ejecución](../extensibility/internals/running-document-table.md).  
  
 En su <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementación, examine el objeto de datos de documento devuelto en `punkDocDataExisting` para determinar si los datos del documento están adecuados para el editor. (Por ejemplo, solo los datos HTML deben mostrarse mediante un editor de HTML.) Si es adecuado, el generador de editores debe proporcionar una segunda vista para los datos. Si el `punkDocDataExisting` parámetro no es `NULL`, es posible ya que el objeto de datos de documento está abierto en otro editor, o, más probable, que los datos del documento ya está abiertos en una vista diferente con el mismo que el editor. Si los datos del documento están abiertos en un editor distinto que no es compatible con el generador de editores, Visual Studio no puede abrir el generador de editores. Para obtener más información, consulte [Cómo: adjuntar vistas de datos del documento](../extensibility/how-to-attach-views-to-document-data.md).


---
title: Creación de diseñadores y editores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a806e434bebb5a561534fb8aec19d16dc9e28ffd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891050"
---
# <a name="create-custom-editors-and-designers"></a>Creación de diseñadores y editores personalizados

El entorno de desarrollo integrado (IDE) de Visual Studio puede hospedar diferentes tipos de editor:

- El editor de núcleo de Visual Studio

- Editores personalizados

- Editores externos

- Diseñadores

La siguiente información le ayuda a elegir el tipo de editor que necesita.

## <a name="types-of-editor"></a>Tipos de editor

Para obtener información acerca del editor de núcleo de Visual Studio, consulte [ampliar los servicios de editor y lenguaje](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Editores personalizados
 Un editor personalizado es aquella que está diseñado para funcionar en circunstancias específicas. Por ejemplo, puede crear un editor cuya función consiste en leer y escribir datos en un repositorio específico, como un servidor Microsoft Exchange. Si desea un editor que funciona con el tipo de proyecto solo o si desea que un editor que tenga solo unos comandos específicos, elija un editor personalizado. Sin embargo, tenga en cuenta que los usuarios no podrán utilizar un editor personalizado para modificar estándar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos.

 Un editor personalizado puede usar un generador de editores y agregar información sobre el editor en el registro. Sin embargo, el tipo de proyecto asociado con el editor personalizado puede crear una instancia del editor personalizado de otras maneras.

 Un editor personalizado puede utilizar la activación en contexto o incrustación simplificada para implementar una vista.

### <a name="external-editors"></a>Editores externos
 Editores externos son editores que no están integrados en Visual Studio, como Microsoft Word, el Bloc de notas o Microsoft FrontPage. Puede llamar a un editor de este tipo si, por ejemplo, va a pasar texto a él desde el VSPackage. Editores externos se registran y se pueden usar fuera de Visual Studio. Cuando llama a un editor externo, y se puede incrustar en una ventana host, a continuación, aparece en una ventana en el IDE. De lo contrario, el IDE crea una ventana independiente para él.

 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método establece la prioridad del documento mediante el uso de la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración. Si el `DP_External` valor se especifica, se puede abrir el archivo con un editor externo.

## <a name="editor-design-decisions"></a>Decisiones de diseño del Editor
 Las siguientes preguntas de diseño le ayudará a elegir el tipo de editor procedimiento adecuado para su aplicación:

- ¿La aplicación guardará sus datos en archivos o no? ¿Si sus datos guardará en archivos, estarán en un formato estándar o personalizado?

   Si usa un formato de archivo estándar, otros tipos de proyecto, además de su proyecto podrá abrir y leer y escribir datos en ellos. Si usa un formato de archivo personalizado, sin embargo, solo el tipo de proyecto será capaz de abrir y leer y escribir datos en ellos.

   Si el proyecto usa archivos, a continuación, debe personalizar el editor estándar. Si no usa archivos de proyecto, sino que usa elementos en una base de datos o en otro repositorio, a continuación, debe crear un editor personalizado.

- ¿Necesita su editor para hospedar controles ActiveX?

   Si el editor que hospeda los controles ActiveX, a continuación, implementar un editor de activación en contexto, tal como se describe en [activación en contexto](../extensibility/in-place-activation.md). Si no hospeda controles ActiveX, a continuación, utilice un editor de incrustación simplificado, o personalizar la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predeterminado.

- ¿Será su editor es compatible con varias vistas? Debe admitir varias vistas si desea que las vistas del editor sea visible al mismo tiempo como editor predeterminado.

   Si el editor debe admitir varias vistas, los datos del documento y los objetos de vista de documento para el editor deben ser objetos independientes. Para obtener más información, consulte [admite varias vistas de documento](../extensibility/supporting-multiple-document-views.md).

   Si el editor admite varias vistas, ¿tiene pensado usar la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principales de implementación de búfer de texto del editor (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto) para el objeto de datos del documento? ¿Es decir, si desea admitir su editor vista side-by-side con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal? La capacidad de hacer esto es la base del Diseñador de formularios...

- ¿Si necesita para hospedar un editor externo, el editor se puede incrustar dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   Si se puede incrustar, debe crear una ventana de host para el editor externo y, a continuación, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método y establezca el <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valor de enumeración para `DP_External`. Si no se puede incrustar el editor, el IDE creará automáticamente una ventana independiente para él.

## <a name="in-this-section"></a>En esta sección

[Tutorial: Crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)\
Explica cómo crear un editor personalizado.

[Tutorial: Agregar características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Explica cómo agregar características a un editor personalizado.

[Configuración de inicialización y metadatos del diseñador](../extensibility/designer-initialization-and-metadata-configuration.md)\
Explica cómo inicializar un diseñador.

[Fuente de alimentación de deshacer a diseñadores](../extensibility/supplying-undo-support-to-designers.md)\
Explica cómo proporcionar soporte para deshacer para diseñadores.

[Colores de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)\
Explica la diferencia entre los colores en el editor básico y en editores personalizados de la sintaxis.

[Datos del documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Explica cómo implementar datos de documentos y vistas de documento en editores personalizados.

## <a name="related-sections"></a>Secciones relacionadas

[Interfaces heredadas en el editor](../extensibility/legacy-interfaces-in-the-editor.md)\
Explica cómo obtener acceso al editor de núcleo por medio de la API heredada.

[Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)\
Explica cómo implementar un servicio de lenguaje.

[Extender otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Explica cómo crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
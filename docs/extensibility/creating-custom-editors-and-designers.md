---
title: "Crear editores personalizados y diseñadores | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 149870d9c9a0a281cb0bba167496cc4c37d6f83a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="creating-custom-editors-and-designers"></a>Crear editores y diseñadores personalizados
El entorno de desarrollo integrado (IDE) de Visual Studio puede alojar diferentes tipos de editor:  
  
-   El editor principal de Visual Studio  
  
-   Editores personalizados  
  
-   Editores externos  
  
-   Diseñadores  
  
 La siguiente información le ayuda a elegir el tipo de editor que necesita.  
  
## <a name="types-of-editor"></a>Tipos de Editor  
 Para obtener información acerca del editor de Visual Studio core, vea [extender el Editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Editores personalizados  
 Un editor personalizado es aquella que está diseñado para funcionar en circunstancias específicas. Por ejemplo, podría crear un editor cuya función consiste en leer y escribir datos en un repositorio específico, como un servidor de Microsoft Exchange. Elija un editor personalizado si desea que un editor que funciona con el tipo de proyecto solo o si desea que un editor con solo unos comandos específicos. Sin embargo, tenga en cuenta que los usuarios no podrán utilizar un editor personalizado para editar estándar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos.  
  
 Un editor personalizado puede utilizar un generador de editores y agregar información sobre el editor en el registro. Sin embargo, el tipo de proyecto asociado con el editor personalizado puede crear una instancia del editor personalizado de otras maneras.  
  
 Un editor personalizado puede utilizar la activación en contexto o incrustar simplificada para implementar una vista.  
  
##### <a name="external-editors"></a>Editores externos  
 Editores externos son editores que no están integrados en Visual Studio, como Microsoft Word, el Bloc de notas o Microsoft FrontPage. Puede llamar a un editor de este tipo si, por ejemplo, va a pasar texto a él desde el VSPackage. Editores externos se registran y se pueden utilizar fuera de Visual Studio. Cuando se llama a un editor externo, y puede incluirse en una ventana host, a continuación, aparece en una ventana en el IDE. De lo contrario, a continuación, el IDE crea una ventana independiente para él.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método establece la prioridad del documento utilizando el <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración. Si el `DP_External` valor se especifica, el archivo puede abrirse en un editor externo.  
  
## <a name="editor-design-decisions"></a>Decisiones de diseño del Editor  
 Las siguientes preguntas de diseño le ayudará a elegir el tipo de editor mejor adecuado para su aplicación:  
  
-   ¿La aplicación guardará sus datos en archivos o no? ¿Si guardará sus datos en archivos, estarán en un formato estándar o personalizado?  
  
     Si usa un formato de archivo estándar, otros tipos de proyecto, además de su proyecto podrá abrir y leer y escribir datos en ellos. Si usa un formato de archivo personalizado, sin embargo, solo el tipo de proyecto será capaz de abrir y leer y escribir datos en ellos.  
  
     Si el proyecto utiliza archivos, debe personalizar el editor estándar. Si el proyecto no usa archivos, sino que usa elementos en una base de datos o en otro diferente, debe crear un editor personalizado.  
  
-   ¿Se necesita el editor hospedar controles ActiveX?  
  
     Si el editor hospeda controles ActiveX, a continuación, implementar un editor de activación en contexto, tal como se describe en [activación en contexto](../extensibility/in-place-activation.md). Si no lo hospedar controles ActiveX, a continuación, utilice un editor de incrustación simplificado, o personalizar la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predeterminado.  
  
-   ¿Será su editor es compatible con varias vistas? Debe admitir varias vistas si desea que las vistas de su editor esté visible al mismo tiempo como el editor predeterminado.  
  
     Si el editor debe admitir varias vistas, los datos del documento y los objetos de vista de documento para el editor deben ser objetos independientes. Para obtener más información, consulte [admitir varias vistas de documento](../extensibility/supporting-multiple-document-views.md).  
  
     Si el editor admite varias vistas, ¿tiene pensado usar la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principales de implementación del búfer del editor de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto) para el objeto de datos de documentos? ¿Es decir, desea admitir su editor vista side-by-side con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal? La capacidad de hacer esto es la base del Diseñador de formularios...  
  
-   ¿Si necesita hospedar un editor externo, el editor se puede incrustar dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Si puede estar incrustado, debe crear una ventana de host para el editor externo y, a continuación, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método y establezca la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valor de enumeración para `DP_External`. Si no se puede incrustar el editor, el IDE crea automáticamente una ventana independiente para él.  
  
## <a name="in-this-section"></a>En esta sección  
 [Tutorial: creación de un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explica cómo crear un editor personalizado.  
  
 [Tutorial: adición de características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explica cómo agregar características a un editor personalizado.  
  
 [Inicialización de diseñador y configuración de metadatos](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explica cómo inicializar un diseñador.  
  
 [Provisión de soporte para deshacer a diseñadores](../extensibility/supplying-undo-support-to-designers.md)  
 Explica cómo proporcionar soporte técnico de deshacer para los diseñadores.  
  
 [Colores de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explica la diferencia entre los colores en el editor principal y en los editores personalizados de la sintaxis.  
  
 [Datos de documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explica cómo implementar datos de documentos y vistas de documentos en editores personalizados.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Interfaces heredadas en el Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explica cómo obtener acceso al editor de núcleos por medio de la API heredada.  
  
 [Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explica cómo implementar un servicio de lenguaje.  
  
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
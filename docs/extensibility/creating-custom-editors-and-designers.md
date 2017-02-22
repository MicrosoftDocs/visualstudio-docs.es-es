---
title: "Creaci&#243;n de dise&#241;adores y editores personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "diseñadores [SDK de Visual Studio]"
  - "editores [Visual Studio SDK], personalizados"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
caps.handback.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n de dise&#241;adores y editores personalizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El entorno de desarrollo integrado \(IDE\) de Visual Studio puede alojar diferentes tipos de editor:  
  
-   El editor principal de Visual Studio  
  
-   Editores personalizados  
  
-   Editores externos  
  
-   Diseñadores  
  
 La siguiente información le ayuda a elegir el tipo de editor que necesita.  
  
## Tipos de Editor  
 Para obtener información sobre el editor principal de Visual Studio, consulte [Extender el Editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md).  
  
##### Editores personalizados  
 Un editor personalizado es aquella que está diseñado para funcionar en circunstancias específicas. Por ejemplo, puede crear un editor cuya función es leer y escribir datos en un repositorio específico, como un servidor de Microsoft Exchange. Elija un editor personalizado si desea que un editor que funciona con el tipo de proyecto solo o si desea que un editor que tiene algunos comandos específicos. Sin embargo, tenga en cuenta que los usuarios no podrán utilizar un editor personalizado para modificar estándar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos.  
  
 Un editor personalizado puede utilizar un generador de editores y agregar información sobre el editor en el registro. Sin embargo, el tipo de proyecto asociado con el editor personalizado puede crear instancias del editor personalizado de otras maneras.  
  
 Un editor personalizado puede utilizar la activación en contexto o incrustación simplificada para implementar una vista.  
  
##### Editores externos  
 Editores externos son editores que no están integrados en Visual Studio, como Microsoft Word, el Bloc de notas o Microsoft FrontPage. Puede llamar a un editor de este tipo si, por ejemplo, va a pasar texto a él desde el VSPackage. Editores externos se registran y se pueden usar fuera de Visual Studio. Cuando se llama a un editor externo, y se puede incrustar en una ventana host, a continuación, aparece en una ventana en el IDE. De lo contrario, el IDE crea una ventana independiente para él.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método establece la prioridad del documento utilizando la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> \(enumeración\). Si el `DP_External` se especifica el valor, se puede abrir el archivo mediante un editor externo.  
  
## Decisiones de diseño del Editor  
 Las cuestiones de diseño siguientes le ayudarán a elegir el tipo de editor mejor para su aplicación:  
  
-   ¿La aplicación guardará sus datos en archivos o no? ¿Si sus datos guardará en archivos, estarán en un formato estándar o personalizado?  
  
     Si utiliza un formato de archivo estándar, otros tipos de proyecto, además de su proyecto podrá abrir y leer y escribir datos en ellos. Si utiliza un formato de archivo personalizado, sin embargo, sólo el tipo de proyecto podrá abrir y leer y escribir datos en ellos.  
  
     Si el proyecto utiliza archivos, debe personalizar el editor estándar. Si el proyecto no usa archivos, sino que usa elementos en una base de datos o en otro diferente, debe crear un editor personalizado.  
  
-   ¿Necesita el editor para hospedar controles ActiveX?  
  
     Si el editor hospeda controles ActiveX, a continuación, implementar un editor de activación en contexto, como se describe en [activación en contexto](../misc/in-place-activation.md). Si no hospeda controles ActiveX, a continuación, utilice un editor de incrustación simplificado, o personalizar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predeterminado.  
  
-   ¿Será su editor es compatible con varias vistas? Debe admitir varias vistas si desea que las vistas de su editor sea visible al mismo tiempo como editor predeterminado.  
  
     Si el editor debe admitir varias vistas, los datos del documento y los objetos de vista de documento para el editor deben ser objetos independientes. Para obtener más información, consulta [Admitir varias vistas del documento](../extensibility/supporting-multiple-document-views.md).  
  
     Si el editor admite varias vistas, ¿tiene pensado utilizar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principales de implementación del búfer del editor de texto \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto\) para el objeto de datos de documentos? ¿Es decir, desea admitir su editor vista side\-by\-side con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal? La capacidad de hacer esto es la base del Diseñador de formularios...  
  
-   ¿Si necesita hospedar un editor externo, el editor se puede incrustar dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Si se puede incrustar, debe crear una ventana host para el editor externo y, a continuación, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> \(método\) y establezca el <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valor de enumeración para `DP_External`. Si no se puede incrustar el editor, el IDE crea automáticamente una ventana independiente para él.  
  
## En esta sección  
 [Tutorial: Crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Explica cómo crear un editor personalizado.  
  
 [Tutorial: Agregar características a un Editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Explica cómo agregar características a un editor personalizado.  
  
 [Inicialización de diseñador y configuración de metadatos](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Explica cómo inicializar un diseñador.  
  
 [Proporciona compatibilidad de deshacer para diseñadores](../extensibility/supplying-undo-support-to-designers.md)  
 Explica cómo proporcionar compatibilidad de deshacer para diseñadores.  
  
 [Colores en los editores personalizados de sintaxis](../extensibility/syntax-coloring-in-custom-editors.md)  
 Explica la diferencia entre los colores en el editor principal y en los editores personalizados de sintaxis.  
  
 [Datos del documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Explica cómo implementar datos de documentos y vistas de documentos en editores personalizados.  
  
## Secciones relacionadas  
 [Interfaces heredadas en el Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Explica cómo obtener acceso al editor de núcleo por medio de la API heredada.  
  
 [Desarrollar un servicio de lenguaje](../extensibility/internals/developing-a-legacy-language-service.md)  
 Explica cómo implementar un servicio de lenguaje.  
  
 [Extensión de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
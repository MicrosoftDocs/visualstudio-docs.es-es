---
title: Creación de editores y diseñadores personalizados Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739476"
---
# <a name="create-custom-editors-and-designers"></a>Crear editores y diseñadores personalizados

El entorno de desarrollo integrado (IDE) de Visual Studio puede hospedar diferentes tipos de editor:

- El editor principal de Visual Studio

- Editores personalizados

- Editores externos

- Diseñadores

La siguiente información le ayuda a elegir el tipo de editor que necesita.

## <a name="types-of-editor"></a>Tipos de editor

Para obtener información sobre el editor principal de Visual Studio, vea [Extender el editor y](../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

### <a name="custom-editors"></a>Editores personalizados
 Un editor personalizado es aquel que está diseñado para trabajar en circunstancias especializadas. Por ejemplo, puede crear un editor cuya función sea leer y escribir datos en un repositorio específico, como un servidor de Microsoft Exchange. Elija un editor personalizado si desea un editor que solo funcione con el tipo de proyecto o si desea un editor que tenga solo unos pocos comandos específicos. Tenga en cuenta, sin embargo, que los usuarios no podrán usar un editor personalizado para editar proyectos estándar. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

 Un editor personalizado puede usar un generador de editores y agregar información sobre el editor al registro. Sin embargo, el tipo de proyecto asociado con el editor personalizado puede crear instancias del editor personalizado de otras maneras.

 Un editor personalizado puede usar la activación in situ o la incrustación simplificada para implementar una vista.

### <a name="external-editors"></a>Editores externos
 Los editores externos son editores que no están integrados en Visual Studio, como Microsoft Word, el Bloc de notas o Microsoft FrontPage. Puede llamar a un editor de este tipo si, por ejemplo, está pasando texto a él desde el VSPackage. Los editores externos se registran a sí mismos y se pueden usar fuera de Visual Studio. Cuando se llama a un editor externo y se puede incrustar en una ventana host, aparece en una ventana del IDE. Si no es así, el IDE crea una ventana independiente para él.

 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método establece la prioridad <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> del documento mediante la enumeración. Si `DP_External` se especifica el valor, un editor externo puede abrir el archivo.

## <a name="editor-design-decisions"></a>Decisiones de diseño del editor
 Las siguientes preguntas de diseño le ayudarán a elegir el tipo de editor que mejor se adapte a su aplicación:

- ¿Guardará su aplicación sus datos en archivos o no? Si va a guardar sus datos en archivos, ¿estarán en un formato personalizado o estándar?

   Si utiliza un formato de archivo estándar, otros tipos de proyecto además de su proyecto podrán abrir y leer/escribir datos en ellos. Sin embargo, si utiliza un formato de archivo personalizado, solo el tipo de proyecto podrá abrir les y leer/escribir datos en ellos.

   Si el proyecto utiliza archivos, debe personalizar el editor estándar. Si el proyecto no utiliza archivos, sino que utiliza elementos en una base de datos u otro repositorio, debe crear un editor personalizado.

- ¿Es necesario que el editor hospede controles ActiveX?

   Si el editor hospeda controles ActiveX, implemente un editor de activación in situ, como se describe en [Activación en contexto.](/visualstudio/misc/in-place-activation?view=vs-2015) Si no hospeda controles ActiveX, utilice un editor de incrustación simplificado o personalice el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predeterminado.

- ¿Su editor admitirá varias vistas? Debe admitir varias vistas si desea que las vistas del editor estén visibles al mismo tiempo que el editor predeterminado.

   Si el editor necesita admitir varias vistas, los datos del documento y los objetos de vista de documento para el editor deben ser objetos independientes. Para obtener más información, consulte [Compatibilidad con varias vistas](../extensibility/supporting-multiple-document-views.md)de documentos.

   Si el editor admite varias vistas, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ¿tiene previsto utilizar la<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> implementación de búfer de texto (objeto) del editor principal para el objeto de datos de documento? Es decir, ¿desea admitir la vista del editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en paralelo con el editor principal? La capacidad de hacer esto es la base del diseñador de formularios..

- Si necesita alojar un editor externo, ¿se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]puede incrustar el editor en el interior?

   Si se puede incrustar, debe crear una ventana host para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> el editor <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> externo y, a continuación, llamar al método y establecer el valor de enumeración en `DP_External`. Si el editor no se puede incrustar, el IDE creará automáticamente una ventana independiente para él.

## <a name="in-this-section"></a>En esta sección

[Tutorial: Crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)\
Explica cómo crear un editor personalizado.

[Tutorial: Agregar características a un editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Explica cómo agregar características a un editor personalizado.

[Inicialización del diseñador y configuración de metadatos](../extensibility/designer-initialization-and-metadata-configuration.md)\
Explica cómo inicializar un diseñador.

[Soporte de deshacer de suministros a los diseñadores](../extensibility/supplying-undo-support-to-designers.md)\
Explica cómo proporcionar soporte de deshacer para diseñadores.

[Coloración de sintaxis en editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)\
Explica la diferencia entre el color de sintaxis en el editor principal y en los editores personalizados.

[Datos de documentos y vista de documentos en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Explica cómo implementar datos de documentos y vistas de documentos en editores personalizados.

## <a name="related-sections"></a>Secciones relacionadas

[Interfaces heredadas en el editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Explica cómo acceder al editor principal mediante la API heredada.

[Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)\
Explica cómo implementar un servicio de lenguaje.

[Ampliar otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Explica cómo crear elementos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]interfaz de usuario que coinciden con el resto de .

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>

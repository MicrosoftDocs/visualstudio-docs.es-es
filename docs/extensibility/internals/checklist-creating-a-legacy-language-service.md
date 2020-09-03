---
title: 'Lista de comprobación: creación de un servicio de lenguaje heredado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709790"
---
# <a name="checklist-create-a-legacy-language-service"></a>Lista de comprobación: creación de un servicio de lenguaje heredado
La siguiente lista de comprobación resume los pasos básicos que debe seguir para crear un servicio de lenguaje para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Editor básico. Para integrar el servicio de lenguaje en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , debe crear un evaluador de expresiones de depuración. Para obtener más información, vea [escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) en la [extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Pasos para crear un servicio de lenguaje

1. Implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - En el VSPackage, implemente la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz para proporcionar el servicio de lenguaje.

    - Haga que su servicio de lenguaje esté disponible en el entorno de desarrollo integrado (IDE) de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación de.

2. Implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz en la clase de servicio de lenguaje principal.

     La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz es el punto de partida de la interacción entre el editor básico y el servicio de lenguaje.

### <a name="optional-features"></a>Características opcionales
 Las siguientes características son opcionales y se pueden implementar en cualquier orden. Estas características aumentan la funcionalidad del servicio de lenguaje.

- Seleccionar el color de la sintaxis

  Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. La implementación de esta interfaz debe ser la información del analizador para devolver la información de color adecuada.

  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método devuelve la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz. Se crea una instancia de un coloreado independiente para cada búfer de texto, por lo que debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz por separado. Para obtener más información, consulte [color de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Ventana de código

  Implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaz para permitir que el servicio de lenguaje reciba la notificación de Cuándo se crea una nueva ventana de código.

  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método devuelve la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaz. Después, el servicio de lenguaje puede Agregar una interfaz de usuario especial a la ventana de código en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . El servicio de lenguaje también puede realizar cualquier procesamiento especial, como agregar un filtro de vista de texto en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Filtro de vista de texto

  Para proporcionar la finalización de instrucciones de IntelliSense en un servicio de lenguaje, debe interceptar algunos comandos que la vista de texto controlaría de otro modo. Para interceptar estos comandos, complete los pasos siguientes:

  - Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar en la cadena de comandos y controlar los comandos del editor.

  - Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método y pase su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación.

  - Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> método al Desasociar de la vista para que estos comandos dejen de pasarse a usted.

  Los comandos que deben administrarse dependen de los servicios que se proporcionan. Para obtener más información, vea [comandos importantes para filtros del servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaz debe implementarse en el mismo objeto que la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.

- Instrucciones completadas

  Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Admite el comando de finalización de instrucciones (es decir, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) y llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz, pasando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz. Para obtener más información, consulte [finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Sugerencias de método

  Implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz para proporcionar datos para la ventana de sugerencia de método.

  Instale el filtro de la vista de texto para controlar los comandos adecuadamente, de modo que sepa cuándo mostrar una ventana de información sobre datos de método. Para obtener más información, vea [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Marcadores de error

  Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Cree los objetos de marcador de error que implementan la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz y llamen al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método, pasando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz del objeto de marcador de error.

  Normalmente, cada marcador de error administra un elemento en la ventana Lista de tareas.

- Elementos de la lista de tareas

  Implemente una clase de elemento de tarea que proporcione la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfaz.

  Implemente una clase de proveedor de tareas que proporcione la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfaz.

  Implemente una clase de enumerador de tareas que proporcione la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfaz.

  Registre el proveedor de tareas con el método de la lista de tareas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .

  Obtenga la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaz llamando al proveedor de servicios del servicio de lenguaje con el GUID de servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  Cree objetos de elemento de tarea y llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> método en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaz cuando haya tareas nuevas o actualizadas.

- Elementos de tarea de comentario

  Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaz para obtener los tokens de tareas de comentario.

  Obtenga una <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaz del <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> servicio.

  Obtenga la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaz desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> método.

  Implemente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfaz para escuchar los cambios en la lista de tokens.

- esquematizar

  Hay varias opciones para admitir la esquematización. Por ejemplo, puede admitir el comando **contraer a definiciones** , proporcionar regiones de esquema controladas por el editor o admitir regiones controladas por el cliente. Para obtener más información, consulte [Cómo: proporcionar compatibilidad ampliada de esquematización en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Registro del servicio de lenguaje

  Para obtener más información sobre cómo registrar un servicio de lenguaje, vea [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md) y [administrar VSPackages](../../extensibility/managing-vspackages.md).

- Ayuda contextual

  Proporcione contexto al editor de una de las siguientes maneras:

  - Proporcione contexto para los marcadores de texto implementando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaz.

  - Proporcione el contexto de todos los usuarios implementando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaz.

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

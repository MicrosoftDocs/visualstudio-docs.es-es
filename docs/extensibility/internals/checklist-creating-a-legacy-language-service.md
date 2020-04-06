---
title: 'Lista de verificación: Creación de un servicio de lenguaje heredado (Legacy Language Service) Microsoft Docs'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709790"
---
# <a name="checklist-create-a-legacy-language-service"></a>Lista de verificación: Crear un servicio de lenguaje heredado
La siguiente lista de comprobación resume los pasos básicos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que debe seguir para crear un servicio de lenguaje para el editor principal. Para integrar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]servicio de lenguaje en , debe crear un evaluador de expresiones de depuración. Para obtener más información, vea [Escribir un evaluador](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) de expresiones CLR en la [extensibilidad](../../extensibility/debugger/visual-studio-debugger-extensibility.md)del depurador de Visual Studio .

## <a name="steps-to-create-a-language-service"></a>Pasos para crear un servicio de idiomas

1. Implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - En el VSPackage, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implemente la interfaz para proporcionar el servicio de lenguaje.

    - Haga que su servicio de lenguaje esté disponible <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> para el entorno de desarrollo integrado (IDE) en su implementación.

2. Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> la interfaz en la clase de servicio de lenguaje principal.

     La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz es el punto de partida de la interacción entre el editor principal y el servicio de lenguaje.

### <a name="optional-features"></a>Características opcionales
 Las siguientes características son opcionales y se pueden implementar en cualquier orden. Estas características aumentan la funcionalidad de su servicio de lenguaje.

- Seleccionar el color de la sintaxis

  Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. La implementación de esta interfaz debe la información del analizador para devolver la información de color adecuada.

  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> devuelve la interfaz. Se crea una instancia de colorante independiente para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> cada búfer de texto, por lo que debe implementar la interfaz por separado. Para obtener más información, consulte [Coloración](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)de sintaxis en un servicio de lenguaje heredado.

- Ventana de código

  Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> la interfaz para permitir que el servicio de lenguaje reciba una notificación de cuándo se crea una nueva ventana de código.

  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> devuelve la interfaz. A continuación, el servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>puede agregar una interfaz de usuario especial a la ventana de código en . El servicio de lenguaje también puede realizar cualquier procesamiento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>especial, como agregar un filtro de vista de texto en .

- Filtro de vista de texto

  Para proporcionar la finalización de instrucciones de IntelliSense en un servicio de lenguaje, debe interceptar algunos de los comandos que la vista de texto controlaría de otro modo. Para interceptar estos comandos, siga estos pasos:

  - Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar en la cadena de comandos y controlar los comandos del editor.

  - Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> al método y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pase la implementación.

  - Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> al método cuando se desasocie de la vista para que estos comandos ya no se le pasen.

  Los comandos que se deben controlar dependen de los servicios que se proporcionan. Para obtener más información, consulte [Comandos importantes para filtros](../../extensibility/internals/important-commands-for-language-service-filters.md)de servicio de lenguaje.

  > [!NOTE]
  > La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaz debe implementarse en <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> el mismo objeto que la interfaz.

- Instrucciones completadas

  Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Admite el comando statement completion <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>(es <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> decir, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ) y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> llama al método en la interfaz, pasando la interfaz. Para obtener más información, consulte Finalización de instrucciones en un servicio de [lenguaje heredado.](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

- Consejos de método

  Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> la interfaz para proporcionar datos para la ventana de sugerencia de método.

  Instale el filtro de vista de texto para controlar los comandos de forma adecuada, de modo que sepa cuándo mostrar una ventana de sugerencia de datos de método. Para obtener más información, consulte [Información de parámetros en un servicio](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)de lenguaje heredado.

- Marcadores de error

  Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Cree los objetos de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> marcador de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> error que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> implementan la interfaz y llaman al método, pasando la interfaz del objeto de marcador de error.

  Normalmente, cada marcador de error administra un elemento en la ventana de lista de tareas.

- Elementos de la lista de tareas

  Implemente una clase de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> elemento de tarea que proporcione la interfaz.

  Implemente una clase de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> proveedor <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> de tareas que proporcione la interfaz y la interfaz.

  Implemente una clase de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> enumerador de tareas que proporcione la interfaz.

  Registre el proveedor de tareas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> con el método de la lista de tareas.

  Obtenga <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> la interfaz llamando al proveedor de servicios <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>del servicio de lenguaje con el GUID del servicio.

  Cree objetos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> elemento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> tarea y llame al método en la interfaz cuando haya tareas nuevas o actualizadas.

- Comentar elementos de tarea

  Utilice <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> la interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaz para obtener los tokens de tarea de comentario.

  Obtenga <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> una interfaz del <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> servicio.

  Obtenga <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> la interfaz del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> método.

  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> la interfaz para escuchar los cambios en la lista de tokens.

- esquematizar

  Hay varias opciones para apoyar la esquematización. Por ejemplo, puede admitir el comando **Contraer a definiciones,** proporcionar regiones de esquema controladas por el editor o admitir regiones controladas por el cliente. Para obtener más información, consulte Cómo: proporcionar compatibilidad de [esquematización ampliada en un servicio](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)de lenguaje heredado.

- Registro del servicio de idiomas

  Para obtener más información acerca de cómo registrar un servicio de lenguaje, vea [Registrar un servicio](../../extensibility/internals/registering-a-legacy-language-service2.md) de lenguaje heredado y Administrar [VSPackages](../../extensibility/managing-vspackages.md).

- Ayuda contextual

  Proporcione contexto al editor de una de las siguientes maneras:

  - Proporcione contexto para los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> marcadores de texto mediante la implementación de la interfaz.

  - Proporcione todo el contexto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> de usuario mediante la implementación de la interfaz.

## <a name="see-also"></a>Vea también
- [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

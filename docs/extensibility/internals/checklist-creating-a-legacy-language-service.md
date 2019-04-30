---
title: 'Lista de comprobación: Creación de un servicio de lenguaje heredado | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7037b49763d4fda844b7692052935a4eee7f7107
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420690"
---
# <a name="checklist-create-a-legacy-language-service"></a>Lista de comprobación: Crear un servicio de lenguaje heredado
La siguiente lista de comprobación resume los pasos básicos que debe seguir para crear un servicio de lenguaje para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor básico. Integrar el servicio de lenguaje en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], debe crear un evaluador de expresiones de depuración. Para obtener más información, consulte [escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) en el [extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Pasos para crear un servicio de lenguaje

1. Implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - En el paquete de VS, implemente el <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz para proporcionar el servicio de lenguaje.

    - Poner el servicio de lenguaje disponibles para el entorno de desarrollo integrado (IDE) en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación.

2. Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz en la clase de servicio de lenguaje principal.

     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz es el punto inicial de la interacción entre el editor básico y el servicio de lenguaje.

### <a name="optional-features"></a>Características opcionales
 Las siguientes características son opcionales y se pueden implementar en cualquier orden. Estas características aumentan la funcionalidad de su servicio de lenguaje.

- Seleccionar el color de la sintaxis

     Implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. La implementación de esta interfaz debe la información del analizador para devolver la información de color apropiado.

     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método devuelve el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz. Se crea una instancia de Coloreador independiente para cada búfer de texto, por lo que debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz por separado. Para obtener más información, consulte [colores de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Ventana Código

     Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaz para habilitar el servicio de lenguaje recibir una notificación cuando se crea una nueva ventana de código.

     El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método devuelve el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaz. El servicio de lenguaje, a continuación, puede agregar la interfaz de usuario especial en la ventana de código de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. El servicio de lenguaje también puede realizar cualquier procesamiento especial, como agregar un filtro de vista de texto en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.

- Filtro de vista de texto

     Para proporcionar la finalización de instrucciones de IntelliSense en un servicio de lenguaje, debe interceptar algunos de los comandos que en caso contrario, controlaría la vista de texto. Para interceptar estos comandos, complete los pasos siguientes:

    - Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar en los comandos del editor de cadena y el identificador de comando.

    - Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método y pase la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación.

    - Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> método cuando se separa de la vista para que estos comandos ya no se pasan a usted.

    Los comandos que deben controlarse dependen de los servicios que se proporcionan. Para obtener más información, consulte [comandos importantes para el lenguaje de filtros del servicio](../../extensibility/internals/important-commands-for-language-service-filters.md).

    > [!NOTE]
    > El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaz debe implementarse en el mismo objeto que el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.

- Instrucciones completadas

     Implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

     Admite el comando de finalización de instrucción (es decir, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) y llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz, pasando el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz. Para obtener más información, consulte [finalización de instrucciones en un servicio de lenguaje heredado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Sugerencias de método

     Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz para proporcionar datos para la ventana de sugerencia de método.

     Instale el filtro de vista de texto para controlar los comandos como corresponda, para que sepa cuándo se debe mostrar una ventana de sugerencia de datos de método. Para obtener más información, consulte [información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Marcadores de error

     Implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

     El error al crear los objetos de marcador que implementan la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz y llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método, pasando el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz del objeto de marcador de error.

     Cada marcador de error administra normalmente un elemento en la ventana Lista de tareas.

- Elementos de lista de tareas

     Implementar una clase de elemento de tarea proporcionando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interfaz.

     Implementar una clase de proveedor de tarea proporcionando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interfaz.

     Implementar una clase de enumerador tarea que proporciona el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interfaz.

     Registrar el proveedor de tareas con la lista de tareas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> método.

     Obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaz llamando al proveedor de servicios del servicio de lenguaje con el GUID del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.

     Cree los objetos de elemento de tarea y llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interfaz cuando hay nuevas o actualizar las tareas.

- Elementos de comentario de tarea

     Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaz para obtener tokens de tareas de comentario.

     Obtener un <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interfaz desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> service.

     Obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interfaz desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> método.

     Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interfaz se escucharán los cambios en la lista de tokens.

- esquematizar

     Hay varias opciones para admitir la esquematización. Por ejemplo, puede admitir el **contraer a definiciones** comando, proporcionan regiones de esquema controlado por el editor o admite regiones controlado por el cliente. Para obtener más información, vea [Cómo: Proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Registro del servicio de lenguaje

     Para obtener más información sobre cómo registrar un servicio de lenguaje, consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md) y [administrar VSPackages](../../extensibility/managing-vspackages.md).

- Ayuda contextual

     Proporcionar contexto al editor de una de las maneras siguientes:

    - Proporcionar contexto para los marcadores de texto mediante la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaz.

    - Proporcione todo el contexto de usuario mediante la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaz.

## <a name="see-also"></a>Vea también
- [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
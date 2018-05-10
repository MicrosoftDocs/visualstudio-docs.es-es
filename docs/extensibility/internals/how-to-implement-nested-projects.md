---
title: 'Cómo: implementar proyectos anidados | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dffef39d735b95cff01ead7087aa8b6286e39004
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-implement-nested-projects"></a>Cómo: implementar proyectos anidados

Cuando se crea un tipo de proyecto anidado haya son un varios pasos adicionales que deben implementarse. Un proyecto principal se toma en algunas de las mismas responsabilidades que tiene la solución para sus proyectos anidados (secundarios). El proyecto principal es un contenedor de proyectos similares a una solución. En concreto, hay varios eventos que se deben generar la solución y por los proyectos primario para generar la jerarquía de proyectos anidados. Estos eventos se describen en el siguiente proceso para crear proyectos anidados.

## <a name="create-nested-projects"></a>Crear proyectos anidados

1.  El entorno de desarrollo integrado (IDE) carga información de inicio y el archivo de proyecto del proyecto principal mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaz. El proyecto principal se crea y se agrega a la solución.

    > [!NOTE]
    > En este momento, es demasiado pronto en el proceso para el proyecto principal crear el proyecto anidado porque el proyecto principal se debe crear antes de pueden crear los proyectos secundarios. Después de esta secuencia, el proyecto principal puede aplicar configuraciones a los proyectos secundarios y los proyectos secundarios pueden obtener información acerca de los proyectos primario si es necesario. Esta secuencia es si es necesario en los clientes como control de código fuente (SCC) y el Explorador de soluciones.

     El proyecto principal debe esperar a que el <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método para ser llamado por el IDE antes de pueda crear su anidados (secundarios) proyecto o proyectos.

2.  Las llamadas IDE `QueryInterface` en el proyecto principal para <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Si esta llamada se ejecuta correctamente, el IDE llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método del elemento primario para abrir todos los proyectos anidados en el proyecto principal.

3.  Las llamadas de proyecto principal el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> método para notificar a los agentes de escucha que anidados proyectos va a crearse. Control de código fuente, por ejemplo, está escuchando en dichos eventos para saber si se producen los pasos en el proceso de creación de soluciones y proyectos en orden. Si los pasos se producen fuera de servicio, la solución podría no esté registrada con el control de código fuente correctamente.

4.  Las llamadas de proyecto principal <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> método o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> método en cada uno de sus proyectos secundarios.

     Se pasa <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> a la `AddVirtualProject` método para indicar que el proyecto (anidado) virtual se debe agregar a la ventana de proyecto, que se excluye de la compilación, se agrega al control de código fuente y así sucesivamente. `VSADDVPFLAGS` le permite controlar la visibilidad de proyecto anidado e indicar qué funcionalidad está asociado a él.

     Si volver a cargar los proyectos secundarios previamente existente que tiene un GUID almacenado en el archivo de proyecto del proyecto principal, las llamadas de proyecto principal del proyecto `AddVirtualProjectEx`. La única diferencia entre `AddVirtualProject` y `AddVirtualProjectEX` es que `AddVirtualProjectEX` tiene un parámetro para habilitar el proyecto principal especificar una por cada instancia `guidProjectID` para el proyecto secundario para habilitar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> a función correctamente.

     Si no hay ningún GUID disponibles, como cuando se agrega un nuevo proyecto anidado, la solución crea uno para el proyecto en el momento en que se agrega al elemento primario. Es responsabilidad del proyecto para conservar ese GUID en su archivo de proyecto del proyecto principal. Si elimina un proyecto anidado, también puede eliminarse el GUID para ese proyecto.

5.  Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> método en cada proyecto secundario del proyecto principal.

     Debe implementar el proyecto principal `IVsParentProject` si desea anidar proyectos. Pero el elemento primario nunca proyecto llamadas `QueryInterface` para `IVsParentProject` incluso si tiene proyectos principales están bajo él. La solución controla la llamada a `IVsParentProject` y, si se implementa, llama `OpenChildren` para crear los proyectos anidados. `AddVirtualProjectEX` siempre se llama desde `OpenChildren`. Nunca se debería llamar el proyecto principal para mantener a la jerarquía de eventos de creación en orden.

6.  Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> método en el proyecto secundario.

7.  Las llamadas de proyecto principal el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> método para notificar a los agentes de escucha que se han creado los proyectos secundarios para el elemento primario.

8.  Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> método en el proyecto principal después de que todos los proyectos secundarios se han abierto.

     Si aún no existe, el proyecto principal crea un GUID para cada proyecto anidado mediante una llamada a `CoCreateGuid`.

    > [!NOTE]
    > `CoCreateGuid` se llamó a una API COM cuando no se creará un GUID. Para obtener más información, vea `CoCreateGuid` y GUID en MSDN Library.

     El proyecto principal almacena este GUID en su archivo de proyecto para recuperar la próxima vez que se abre en el IDE. Vea el paso 4 para obtener más información relativa a la que realiza la llamada de `AddVirtualProjectEX` para recuperar la `guidProjectID` para el proyecto secundario.

9. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> , a continuación, se llama el método para el elemento primario ItemID que por convención delegue en para el proyecto anidado. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera las propiedades del nodo que se anida un proyecto que se desea delegar en cuando se llama en el elemento primario.

     Dado que los proyectos primarios y secundarios se crean instancias mediante programación, puede establecer propiedades para proyectos anidados en este momento.

    > [!NOTE]
    > No sólo se recibe la información de contexto desde el proyecto anidado, pero también puede preguntar si el proyecto principal tiene cualquier contexto para ese elemento mediante la comprobación de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. De esa manera, puede agregar atributos adicionales de Ayuda dinámica y opciones de menú específicas para proyectos anidados individuales.

10. La jerarquía se crea para su presentación en el Explorador de soluciones con una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> método.

     Pasar la jerarquía en el entorno a través de `GetNestedHierarchy` para generar la jerarquía para su presentación en el Explorador de soluciones. De esta manera, la solución sabe que el proyecto existe y puede administrarse para crear mediante el Administrador de compilación o puede permitir que los archivos del proyecto se deben colocar en el control de código fuente.

11. Cuando se hayan creado todos los proyectos anidados de Proyecto1, control se ha pasado a la solución y el proceso se repite para Proyecto2.

     Se produce el mismo proceso para la creación de proyectos anidados para los proyectos secundarios que tiene un elemento secundario. En este caso, si BuildProject1, que es un elemento secundario de Proyecto1, tenía proyectos secundarios, se podría crear después BuildProject1 y antes de Proyecto2. El proceso es recursiva y la jerarquía se genera desde arriba hacia abajo.

     Cuando se cierra un proyecto anidado porque el usuario ha cerrado la solución o específico del proyecto, el otro método en `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, se llama. El proyecto principal encapsula las llamadas a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> método con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> métodos para notificar a los agentes de escucha de eventos de la solución que se está cerrando los proyectos anidados.

Los temas siguientes tratan con varios otros conceptos que debe considerar al implementar proyectos anidados:

- [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Compatibilidad del Asistente para proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementación del control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrado del cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vea también

- [Adición de elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registro de plantillas para proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
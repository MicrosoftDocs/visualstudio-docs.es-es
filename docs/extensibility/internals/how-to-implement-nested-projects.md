---
title: 'Cómo: implementar proyectos anidados | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b1ac3c147962b943499172435c3f601115d36a9
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905349"
---
# <a name="how-to-implement-nested-projects"></a>Cómo: implementar proyectos anidados

Al crear un tipo de proyecto anidado, hay varios pasos adicionales que se deben implementar. Un proyecto primario realiza algunas de las mismas responsabilidades que tiene la solución para sus proyectos anidados (secundarios). El proyecto principal es un contenedor de proyectos similar a una solución. En concreto, hay varios eventos que debe generar la solución y los proyectos primarios para compilar la jerarquía de proyectos anidados. Estos eventos se describen en el siguiente proceso para crear proyectos anidados.

## <a name="create-nested-projects"></a>Crear proyectos anidados

1. El entorno de desarrollo integrado (IDE) carga el archivo de proyecto y la información de inicio del proyecto primario llamando a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaz. El proyecto primario se crea y se agrega a la solución.

    > [!NOTE]
    > En este momento, es demasiado temprano en el proceso para que el proyecto primario cree el proyecto anidado porque se debe crear el proyecto primario antes de que se puedan crear los proyectos secundarios. Después de esta secuencia, el proyecto primario puede aplicar la configuración a los proyectos secundarios y los proyectos secundarios pueden adquirir información de los proyectos primarios si es necesario. Esta secuencia es si es necesaria en clientes como control de código fuente (SCC) y **Explorador de soluciones**.

     El proyecto primario debe esperar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> que el IDE llame al método antes de poder crear su proyecto o proyectos anidados (secundarios).

2. El IDE llama a `QueryInterface` en el proyecto primario para <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Si esta llamada se realiza correctamente, el IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método del elemento primario para abrir todos los proyectos anidados del proyecto primario.

3. El proyecto primario llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> método para notificar a los agentes de escucha que los proyectos anidados están a punto de crearse. SCC, por ejemplo, está escuchando los eventos para saber si los pasos del proceso de creación de la solución y el proyecto se están produciendo en orden. Si los pasos se producen sin orden, es posible que la solución no esté registrada correctamente con el control de código fuente.

4. El proyecto primario llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> método o al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> método en cada uno de sus proyectos secundarios.

     Se pasa <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> al `AddVirtualProject` método para indicar que el proyecto virtual (anidado) debe agregarse a la ventana del proyecto, excluirse de la compilación, agregarse al control de código fuente, etc. `VSADDVPFLAGS`permite controlar la visibilidad del proyecto anidado e indicar qué funcionalidad está asociada.

     Si vuelve a cargar un proyecto secundario existente que tiene un GUID del proyecto almacenado en el archivo de proyecto del proyecto primario, el proyecto primario llama a `AddVirtualProjectEx` . La única diferencia entre `AddVirtualProject` y `AddVirtualProjectEX` es que `AddVirtualProjectEX` tiene un parámetro para permitir que el proyecto primario especifique un por instancia `guidProjectID` para que el proyecto secundario habilite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> funcione correctamente.

     Si no hay ningún GUID disponible, como cuando se agrega un nuevo proyecto anidado, la solución crea uno para el proyecto en el momento en que se agrega al elemento primario. Es responsabilidad del proyecto primario conservar el GUID del proyecto en su archivo de proyecto. Si elimina un proyecto anidado, también se puede eliminar el GUID de ese proyecto.

5. El IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> método en cada proyecto secundario del proyecto primario.

     El proyecto primario debe implementar `IVsParentProject` si desea anidar proyectos. Pero el proyecto primario nunca llama a `QueryInterface` para `IVsParentProject` aunque tenga proyectos primarios por debajo de él. La solución controla la llamada a `IVsParentProject` y, si se implementa, llama `OpenChildren` a para crear los proyectos anidados. `AddVirtualProjectEX`siempre se llama a desde `OpenChildren` . Nunca debe ser llamado por el proyecto primario para mantener los eventos de creación de la jerarquía en orden.

6. El IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> método en el proyecto secundario.

7. El proyecto primario llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> método para notificar a los agentes de escucha que se han creado los proyectos secundarios del elemento primario.

8. El IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> método en el proyecto primario después de que todos los proyectos secundarios se hayan abierto.

     Si aún no existe, el proyecto primario crea un GUID para cada proyecto anidado mediante una llamada a `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid`es una API de COM a la que se llama cuando se va a crear un GUID. Para obtener más información, vea `CoCreateGuid` y GUID en MSDN Library.

     El proyecto primario almacena este GUID en el archivo de proyecto que se va a recuperar la próxima vez que se abra en el IDE. Vea el paso 4 para obtener más información relacionada con la llamada de `AddVirtualProjectEX` para recuperar el del `guidProjectID` proyecto secundario.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>A continuación, se llama al método para el elemento primario Itemid que, por Convención, delega en el proyecto anidado. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Recupera las propiedades del nodo que anida un proyecto en el que desea delegar cuando se llama en el elemento primario.

     Dado que se crean instancias de los proyectos primarios y secundarios mediante programación, puede establecer las propiedades de los proyectos anidados en este momento.

    > [!NOTE]
    > No solo recibe la información de contexto del proyecto anidado, sino que también puede preguntar si el proyecto primario tiene algún contexto para ese elemento comprobando [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). De este modo, puede agregar atributos de ayuda dinámicos adicionales y opciones de menú específicas de proyectos anidados individuales.

10. La jerarquía se crea para su presentación en **Explorador de soluciones** con una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> método.

     La jerarquía se pasa al entorno a través de `GetNestedHierarchy` para compilar la jerarquía que se va a mostrar en explorador de soluciones. De esta manera, la solución sabe que el proyecto existe y se puede administrar para compilarlo mediante el administrador de compilación o puede permitir que los archivos del proyecto se pongan bajo control de código fuente.

11. Cuando se han creado todos los proyectos anidados de Project1, el control se devuelve a la solución y el proceso se repite para Proyecto2.

     Este mismo proceso para crear proyectos anidados se produce para un proyecto secundario que tiene un elemento secundario. En este caso, si BuildProject1, que es un elemento secundario de Project1, tuviera proyectos secundarios, se crearían después de BuildProject1 y antes de Proyecto2. El proceso es recursivo y la jerarquía se compila de arriba abajo.

     Cuando se cierra un proyecto anidado porque el usuario cerró la solución o el propio proyecto específico, se llama al otro método de `IVsParentProject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> ,. El proyecto primario ajusta las llamadas al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> método con los <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> métodos y para notificar a los agentes de escucha los eventos de solución que se cierran en los proyectos anidados.

En los temas siguientes se tratan otros conceptos que se deben tener en cuenta al implementar proyectos anidados:

- [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Compatibilidad del asistente con proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementar el control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrar el cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vea también

- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Lista de comprobación: crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Archivo del asistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

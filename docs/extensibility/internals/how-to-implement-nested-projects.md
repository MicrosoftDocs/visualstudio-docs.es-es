---
title: 'Cómo: Implementar Proyectos Anidados ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707984"
---
# <a name="how-to-implement-nested-projects"></a>Cómo: Implementar proyectos anidados

Al crear un tipo de proyecto anidado, hay varios pasos adicionales que se deben implementar. Un proyecto primario asume algunas de las mismas responsabilidades que la solución tiene para sus proyectos anidados (secundarios). El proyecto primario es un contenedor de proyectos similar a una solución. En particular, hay varios eventos que debe generar la solución y los proyectos primarios para compilar la jerarquía de proyectos anidados. Estos eventos se describen en el siguiente proceso para crear proyectos anidados.

## <a name="create-nested-projects"></a>Crear proyectos anidados

1. El entorno de desarrollo integrado (IDE) carga el archivo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> proyecto principal y la información de inicio llamando a la interfaz. El proyecto primario se crea y se agrega a la solución.

    > [!NOTE]
    > En este punto, es demasiado temprano en el proceso para que el proyecto primario cree el proyecto anidado porque el proyecto primario debe crearse antes de que se puedan crear los proyectos secundarios. Siguiendo esta secuencia, el proyecto primario puede aplicar la configuración a los proyectos secundarios y los proyectos secundarios pueden adquirir información de los proyectos primarios si es necesario. Esta secuencia es si es necesaria para clientes como el control de código fuente (SCC) y el **Explorador**de soluciones .

     El proyecto primario debe <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> esperar a que el IDE llame al método para poder crear su proyecto o proyectos anidados (secundarios).

2. El IDE `QueryInterface` llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>proyecto primario para . Si esta llamada se realiza correctamente, el IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método del elemento primario para abrir todos los proyectos anidados para el proyecto primario.

3. El proyecto primario <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> llama al método para notificar a los agentes de escucha que los proyectos anidados están a punto de crearse. SCC, por ejemplo, está escuchando esos eventos para saber si los pasos en la solución y el proceso de creación de proyectos se están produciendo en orden. Si los pasos se producen fuera de servicio, es posible que la solución no se registre correctamente con el control de código fuente.

4. El proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> primario llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> al método o al método en cada uno de sus proyectos secundarios.

     Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> pasa `AddVirtualProject` al método para indicar que el proyecto virtual (anidado) se debe agregar a la ventana del proyecto, se excluye de la compilación, se agrega al control de código fuente, etc. `VSADDVPFLAGS`le permite controlar la visibilidad del proyecto anidado e indicar qué funcionalidad está asociada a él.

     Si vuelve a cargar un proyecto secundario existente anteriormente que tiene un GUID `AddVirtualProjectEx`de proyecto almacenado en el archivo de proyecto del proyecto primario, el proyecto primario llama . La única `AddVirtualProject` diferencia `AddVirtualProjectEX` entre `AddVirtualProjectEX` y es que tiene un parámetro `guidProjectID` para permitir que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> proyecto primario especifique una instancia por instancia para que el proyecto secundario habilite y funcione correctamente.

     Si no hay ningún GUID disponible, como cuando se agrega un nuevo proyecto anidado, la solución crea uno para el proyecto en el momento en que se agrega al elemento primario. Es responsabilidad del proyecto primario conservar ese GUID del proyecto en su archivo de proyecto. Si elimina un proyecto anidado, también se puede eliminar el GUID de ese proyecto.

5. El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> llama al método en cada proyecto secundario del proyecto primario.

     El proyecto primario `IVsParentProject` debe implementarse si desea anidar proyectos. Pero el proyecto `QueryInterface` principal `IVsParentProject` nunca requiere incluso si tiene proyectos primarios debajo de él. La solución controla la llamada y, `IVsParentProject` `OpenChildren` si se implementa, llama para crear los proyectos anidados. `AddVirtualProjectEX`siempre se `OpenChildren`llama desde . Nunca debe ser llamado por el proyecto primario para mantener los eventos de creación de jerarquía en orden.

6. El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> llama al método en el proyecto secundario.

7. El proyecto primario <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> llama al método para notificar a los agentes de escucha que se han creado los proyectos secundarios para el elemento primario.

8. El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> llama al método en el proyecto primario después de que se han abierto todos los proyectos secundarios.

     Si aún no existe, el proyecto primario crea un `CoCreateGuid`GUID para cada proyecto anidado llamando a .

    > [!NOTE]
    > `CoCreateGuid`es una API COM a la que se llama cuando se va a crear un GUID. Para obtener más `CoCreateGuid` información, consulte GUID y GUID en MSDN Library.

     El proyecto primario almacena este GUID en su archivo de proyecto que se recuperará la próxima vez que se abra en el IDE. Consulte el paso 4 para obtener `AddVirtualProjectEX` más información `guidProjectID` relacionada con la llamada de recuperar el proyecto secundario.

9. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> continuación, se llama al método para el elemento primario ItemID que por convención se delegue en el proyecto anidado. Recupera <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> las propiedades del nodo que anida un proyecto en el que desea delegar cuando se llama en el elemento primario.

     Dado que los proyectos primarios y secundarios se crean instancias mediante programación, puede establecer propiedades para proyectos anidados en este momento.

    > [!NOTE]
    > No solo recibe la información de contexto del proyecto anidado, sino que también puede preguntar si el proyecto primario tiene algún contexto para ese elemento comprobando [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). De este modo, puede agregar atributos de ayuda dinámicos adicionales y opciones de menú específicas de proyectos anidados individuales.

10. La jerarquía se compila **Solution Explorer** para su presentación <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> en el Explorador de soluciones con una llamada al método.

     Pasar la jerarquía al `GetNestedHierarchy` entorno para compilar la jerarquía para su presentación en el Explorador de soluciones. De esta manera, la solución sabe que el proyecto existe y puede ser administrado para compilar por el administrador de compilación, o puede permitir que los archivos del proyecto se pongan bajo control de código fuente.

11. Cuando se han creado todos los proyectos anidados para Project1, el control se devuelve a la solución y el proceso se repite para Project2.

     Este mismo proceso para crear proyectos anidados se produce para un proyecto secundario que tiene un elemento secundario. En este caso, si BuildProject1, que es un elemento secundario de Project1, tenía proyectos secundarios, se crearían después de BuildProject1 y antes de Project2. El proceso es recursivo y la jerarquía se crea de arriba hacia abajo.

     Cuando se cierra un proyecto anidado porque el usuario cerró la `IVsParentProject`solución o el propio proyecto específico, se llama al otro método en , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, . El proyecto primario ajusta <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> las llamadas al método con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> y los métodos para notificar a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> agentes de escucha a los eventos de solución que los proyectos anidados se están cerrando.

Los temas siguientes tratan con varios otros conceptos a tener en cuenta al implementar proyectos anidados:

- [Consideraciones para descargar y recargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Soporte de asistente sin asistentes para proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementar el control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrar el cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vea también

- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar plantillas de proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [Lista de verificación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Archivo Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

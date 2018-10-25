---
title: 'Cómo: implementar proyectos anidados | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df380078a2fa04c8c36db6f2def7aa89c7a11807
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817007"
---
# <a name="how-to-implement-nested-projects"></a>Cómo: implementar proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando se crea un tipo de proyecto anidado no existe es un varios pasos adicionales que deben implementarse. Un proyecto principal que se tarda en algunas de las mismas responsabilidades que tiene la solución para sus proyectos anidados (secundarios). El proyecto principal es un contenedor de proyectos similares a una solución. En concreto, hay varios eventos que se deben generar la solución y los proyectos primario para crear la jerarquía de proyectos anidados. Estos eventos se describen en el siguiente proceso para la creación de proyectos anidados.  
  
### <a name="to-create-nested-projects"></a>Para crear proyectos anidados  
  
1. El entorno de desarrollo integrado (IDE) carga la información de inicio y el archivo de proyecto del proyecto principal mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaz. El proyecto principal se crea y se agrega a la solución.  
  
   > [!NOTE]
   >  En este momento, es demasiado pronto en el proceso para el proyecto principal crear el proyecto anidado porque se debe crear el proyecto principal antes de que se pueden crear los proyectos secundarios. Siguiendo esta secuencia, el proyecto principal puede aplicar configuraciones a los proyectos secundarios y los proyectos secundarios pueden obtener información acerca de los proyectos principales si es necesario. Esta secuencia es si es necesario en los clientes como control de código fuente (SCC) y el Explorador de soluciones.  
  
    El proyecto principal se debe esperar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método para ser llamado por el IDE antes de pueda crear su anidados (secundarios) proyecto o proyectos.  
  
2. Las llamadas IDE `QueryInterface` en el proyecto primario para <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Si esta llamada se realiza correctamente, las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método del elemento primario para abrir todos los proyectos anidados en el proyecto principal.  
  
3. Las llamadas de proyecto primario el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> método para notificar a los agentes de escucha que anidados proyectos está a punto de crearse. Control de código fuente, por ejemplo, está escuchando a esos eventos para saber si se producen los pasos descritos en el proceso de creación de soluciones y proyectos en orden. Si los pasos se producen fuera de servicio, la solución es posible que no esté registrada con el control de código fuente correctamente.  
  
4. Las llamadas de proyecto primario <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> método o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> método en cada uno de sus proyectos secundarios.  
  
    Pasa <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> a la `AddVirtualProject` método para indicar que el proyecto virtual (anidado) debe agregarse a la ventana de proyecto, excluida de la compilación, se agrega al control de código fuente y así sucesivamente. `VSADDVPFLAGS` le permite controlar la visibilidad del proyecto anidado e indican qué funcionalidad está asociada con él.  
  
    Si volver a cargar un proyecto secundario existente que tiene un proyecto de GUID almacenado en el archivo de proyecto del proyecto principal, las llamadas de proyecto primario `AddVirtualProjectEx`. La única diferencia entre `AddVirtualProject` y `AddVirtualProjectEX` es que `AddVirtualProjectEX` tiene un parámetro para habilitar el proyecto principal especificar una por cada instancia `guidProjectID` para el proyecto secundario para habilitar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> a función correctamente.  
  
    Si no hay ningún GUID disponibles, como cuando se agrega un nuevo proyecto anidado, la solución crea uno para el proyecto en el momento en que se agrega al elemento primario. Es responsabilidad del proyecto para conservar ese GUID en su archivo de proyecto del proyecto principal. Si elimina un proyecto anidado, también puede eliminarse el GUID para ese proyecto.  
  
5. Las llamadas IDE el `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` método en cada proyecto secundario del proyecto primario.  
  
    Debe implementar el proyecto principal `IVsParentProject` si desea anidar los proyectos. Pero el elemento primario del proyecto nunca llama a `QueryInterface` para `IVsParentProject` incluso si tiene proyectos principales debajo de ella. La solución controla la llamada a `IVsParentProject` y, si se implementa, se llama a `OpenChildren` para crear los proyectos anidados. `AddVirtualProjectEX` siempre se llama desde `OpenChildren`. Nunca se debería llamar el proyecto principal para mantener a la jerarquía de eventos de creación en orden.  
  
6. Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> método en el proyecto secundario.  
  
7. Las llamadas de proyecto primario el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> método para notificar a los agentes de escucha que se han creado los proyectos secundarios para el elemento primario.  
  
8. Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> método en el proyecto principal después de que todos los proyectos secundarios se han abierto.  
  
    Si no existe, el proyecto principal crea un GUID para cada proyecto anidado mediante una llamada a `CoCreateGuid`.  
  
   > [!NOTE]
   >  `CoCreateGuid` se llama a una API COM cuando es necesario crear un GUID. Para obtener más información, consulte `CoCreateGuid` y GUID en MSDN Library.  
  
    El proyecto principal almacena este GUID en su archivo de proyecto que va a recuperar la próxima vez que se abre en el IDE. Vea el paso 4 para obtener más información relativa a la llamada de `AddVirtualProjectEX` para recuperar el `guidProjectID` para el proyecto secundario.  
  
9. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> , a continuación, se llama al método para el elemento primario ItemID que por convención, delegar en el proyecto anidado. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera las propiedades del nodo que se anida un proyecto que desee delegar en cuando se llama en el elemento primario.  
  
     Dado que los proyectos primarios y secundarios se crean instancias mediante programación, puede establecer propiedades para proyectos anidados en este momento.  
  
    > [!NOTE]
    >  No solo recibir la información de contexto desde el proyecto anidado, pero también puede hacer si el proyecto principal tiene cualquier contexto de ese elemento comprobando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. De esa manera, puede agregar atributos adicionales de Ayuda dinámica y las opciones de menú específicas para proyectos anidados individuales.  
  
10. La jerarquía se crea para su presentación en el Explorador de soluciones con una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> método.  
  
     Pasar la jerarquía para el entorno a través de `GetNestedHierarchy` para crear la jerarquía para su presentación en el Explorador de soluciones. De esta manera, la solución sabe que existe y puede administrarse mediante el Administrador de compilación para compilar el proyecto o puede permitir que los archivos del proyecto que se puede poner bajo control de código fuente.  
  
11. Cuando se han creado todos los proyectos anidados de Project1, control se pasa a la solución y el proceso se repite para Proyecto2.  
  
     Este mismo proceso para la creación de proyectos anidados se produce para un proyecto secundario que tiene un elemento secundario. En este caso, si BuildProject1, que es un elemento secundario de Project1, tenía los proyectos secundarios, se podría crear después BuildProject1 y antes de Proyecto2. El proceso es recursiva y la jerarquía se crea a partir de la parte superior hacia abajo.  
  
     Cuando se cierra un proyecto anidado porque el usuario ha cerrado la solución o específico del proyecto, el otro método en `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, se llama. El proyecto principal encapsula las llamadas a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> método con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> métodos para notificar a los agentes de escucha de eventos de la solución que se está cerrando los proyectos anidados.  
  
    Los temas siguientes tratan con varios otros conceptos que debe considerar al implementar proyectos anidados:  
  
    [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
    [Compatibilidad del Asistente para proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
    [Implementación del control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
    [Filtrado del cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Vea también  
 [Agregar elementos a la Agregar nuevo elemento de los cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)


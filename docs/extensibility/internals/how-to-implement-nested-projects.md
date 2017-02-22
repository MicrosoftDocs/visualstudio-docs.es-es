---
title: "C&#243;mo: implementar proyectos anidados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos anidados, implementar"
  - "proyectos [Visual Studio SDK] de anidamiento"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: implementar proyectos anidados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando se crea un tipo de proyecto anidada existen varios pasos adicionales que deben implementar.  Un proyecto primario toma en algunas de las mismas responsabilidades que la solución tiene para sus proyectos \(secundarios\) anidados.  El proyecto principal es un contenedor de proyectos similares a una solución.  En concreto, hay varios eventos que se deben activar mediante la solución y los proyectos primarios de compilar la jerarquía de proyectos anidados.  Estos eventos se describen en el siguiente proceso para crear proyectos anidados.  
  
### Para crear proyectos anidados  
  
1.  El entorno \(IDE\) de desarrollo integrado carga información principal del archivo de proyecto y de inicio de proyecto llamando a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> .  El proyecto principal se crea y se agrega a la solución.  
  
    > [!NOTE]
    >  En este punto, está demasiado pronto en el proceso para que el proyecto principal cree el proyecto anidadas porque el proyecto principal se debe crear antes de que los proyectos secundarios se pueden crear.  Después de esta secuencia, el proyecto principal puede aplicar valores a los proyectos secundarios y proyectos secundarios pueden adquirir información de proyectos primarios si es necesario.  Esta secuencia es si se necesita activado por clientes como control de código fuente \(SCC\) y el explorador de soluciones.  
  
     El proyecto principal debe esperar el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> que se denomine el IDE antes de poder crear su proyecto o proyectos \(secundarios\) anidados.  
  
2.  El IDE llama `QueryInterface` en el proyecto principal para <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>.  Si esta llamada se realiza correctamente, el IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> primario para abrir todos los proyectos anidados para el proyecto principal.  
  
3.  El proyecto principal llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> para notificar a los agentes de escucha que los proyectos anidados están a punto de ser creados.  El SCC, por ejemplo, escuchando los eventos para saber si los pasos del proceso de creación de solución y de proyecto se producen en orden.  Si los pasos producen fuera de servicio, la solución no se puede registrar con el control de código fuente correctamente.  
  
4.  El proyecto principal llama a método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> o el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> en cada uno de los proyectos secundarios.  
  
     Pasa <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> al método de `AddVirtualProject` para indicar que el proyecto \(anidada\) virtual se debe agregar a la ventana del proyecto, excluido de compilación, agregada al control de código fuente, etc.  `VSADDVPFLAGS` permite controlar la visibilidad de proyectos anidados e indicar qué funcionalidad está asociado.  
  
     Si se vuelve a cargar un proyecto secundario previamente existente que tiene un proyecto GUID almacenado en el archivo del proyecto principal de proyectos, proyecto primario llama `AddVirtualProjectEx`.  La única diferencia entre `AddVirtualProject` y `AddVirtualProjectEX` es que `AddVirtualProjectEX` tiene un parámetro para habilitar el proyecto principal de especificar por la instancia `guidProjectID` para que el proyecto secundario permite a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> y a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> para funcionar correctamente.  
  
     Si no hay ningún GUID disponibles, como cuando se agrega un nuevo proyecto anidadas, la solución crea uno para el proyecto cuando se agrega al elemento primario.  Es responsabilidad del proyecto principal de conservar ese proyecto GUID en el archivo de proyecto.  Si elimina un proyecto anidados, GUID para ese proyecto también puede eliminarse.  
  
5.  El IDE llama al método de `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` en cada proyecto secundario de proyecto principal.  
  
     El proyecto principal debe implementar `IVsParentProject` si desea anidar proyectos.  Pero el proyecto principal nunca llama a `QueryInterface` para `IVsParentProject` aunque tenga proyectos primarios debajo de él.  La solución controla la llamada a `IVsParentProject` y, si se implementa, llama a `OpenChildren` para crear proyectos anidados.  `AddVirtualProjectEX` siempre se llama de `OpenChildren`.  Nunca debe llamar al proyecto principal de mantener los eventos de creación de la jerarquía en orden.  
  
6.  El IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> en el proyecto secundario.  
  
7.  El proyecto principal llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> para notificar a los agentes de escucha que los proyectos secundarios para el elemento primario se han creado.  
  
8.  El IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> en el proyecto principal después de que todos se han abierto proyectos secundarios.  
  
     Si no existe, el proyecto principal crea GUID para cada proyecto anidada llamando a `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid` es una API COM denominado cuando el GUID debe crearse.  Para obtener más información, vea `CoCreateGuid` y GUID en MSDN Library.  
  
     El proyecto principal almacena este GUID en el archivo de proyecto que se recuperará la próxima vez que se abra en el IDE.  Vea el paso 4 para obtener más información sobre la llamada de `AddVirtualProjectEX` para recuperar `guidProjectID` para el proyecto secundario.  
  
9. El método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> se llama para el ItemID primario que de convención se delega en el proyecto anidados.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera las propiedades del nodo que anida un proyecto en el que desee delegar cuando se llama al elemento primario.  
  
     Dado que los proyectos primarios y secundarios se crean instancias mediante programación, puede establecer las propiedades de los proyectos anidados en este punto.  
  
    > [!NOTE]
    >  No solo recibe información de contexto del proyecto anidadas, pero también puede preguntar si el proyecto principal tiene cualquier contexto para ese elemento comprobando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  De ese modo, puede agregar atributos dinámicos adicionales y las opciones del menú Ayuda específicos de proyectos anidados individuales.  
  
10. La jerarquía se compila para la presentación en el explorador de soluciones con una llamada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> .  
  
     Pasa la jerarquía al entorno con `GetNestedHierarchy` para compilar la jerarquía para la presentación en el explorador de soluciones.  De esta manera, la solución sabe que el proyecto existe y se puede administrar para compilar por el administrador de compilación, o puede permitir los archivos del proyecto se sometido a control de código fuente.  
  
11. Cuando todos los proyectos anidados para Project1 se han creado, el control pasa de nuevo a la solución y el proceso se repite para Project2.  
  
     Este mismo proceso para crear proyectos anidados se produce para un proyecto secundario que tenga un elemento secundario.  En este caso, si BuildProject1, que es un elemento secundario de Project1, tuviera proyectos secundarios, crearían después de BuildProject1 y antes de Project2.  El proceso es recursiva y la jerarquía se compila desde la parte superior siguiente.  
  
     Cuando se cierra un proyecto anidadas porque cerró el usuario la solución o el proyecto concreto propio, el otro método de `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, se denomina.  El proyecto primario ajusta llamadas al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> y los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> para notificar a los agentes de escucha los eventos de la solución que se están cerrados proyectos anidados.  
  
 Los temas siguientes tratan con otros conceptos para tener en cuenta al implementar proyectos anidados:  
  
 [Consideraciones para descargar y volver a cargar proyectos anidados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Admite el Asistente para proyectos anidados](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementación de control de comandos para proyectos anidados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Filtrar el cuadro de diálogo AddItem para proyectos anidados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## Vea también  
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)
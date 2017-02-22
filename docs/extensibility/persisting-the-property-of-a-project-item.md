---
title: "Conservar la propiedad de un elemento de proyecto | Microsoft Docs"
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
  - "propiedades, agregar a un elemento de proyecto"
  - "elementos de proyecto, agregar propiedades"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Conservar la propiedad de un elemento de proyecto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede conservar una propiedad que se agrega a un elemento de proyecto, como el autor de un archivo de origen. Para ello, puede almacenar la propiedad en el archivo de proyecto.  
  
 El primer paso para conservar una propiedad en un archivo de proyecto es obtener la jerarquía del proyecto como un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz. Puede obtener esta interfaz mediante la automatización o mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Una vez que obtenga la interfaz, se puede utilizar para determinar qué elemento de proyecto seleccionado. Una vez que el identificador del elemento de proyecto, puede usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> para agregar la propiedad.  
  
 En los procedimientos siguientes, conservar la propiedad VsPkg.cs `Author` con el valor `Tom` en el archivo de proyecto.  
  
### Para obtener la jerarquía del proyecto con el objeto DTE  
  
1.  Agregue el código siguiente a su VSPackage:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### Para conservar la propiedad de elemento de proyecto con el objeto DTE  
  
1.  Agregue el siguiente código para el código proporcionado en el método en el procedimiento anterior:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Para obtener la jerarquía del proyecto mediante IVsMonitorSelection  
  
1.  Agregue el código siguiente a su VSPackage:  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### Para conservar la propiedad de elemento de proyecto seleccionado, dada la jerarquía del proyecto  
  
1.  Agregue el siguiente código para el código proporcionado en el método en el procedimiento anterior:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Para comprobar que se conserva la propiedad  
  
1.  Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, abra o cree una solución.  
  
2.  Seleccione el proyecto de elemento VsPkg.cs en **el Explorador de soluciones**.  
  
3.  Utilice un punto de interrupción o de lo contrario, determinar que se ha cargado el VSPackage y que ejecuta SetItemAttribute.  
  
    > [!NOTE]
    >  Puede cargar automáticamente un VSPackage en el contexto de la interfaz de usuario <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>. Para obtener más información, consulta [Cargar VSPackages](../extensibility/loading-vspackages.md).  
  
4.  Cerrar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, abra el archivo de proyecto en el Bloc de notas. Debería ver la etiqueta \< Author \> con el valor Tom, como sigue:  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## Vea también  
 [Herramientas personalizadas](../extensibility/internals/custom-tools.md)
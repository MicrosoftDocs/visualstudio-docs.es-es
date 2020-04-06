---
title: Persistiendo la propiedad de un elemento de proyecto Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702204"
---
# <a name="persist-the-property-of-a-project-item"></a>Persistir la propiedad de un elemento de proyecto
Es posible que desee conservar una propiedad que agregue a un elemento de proyecto, como el autor de un archivo de origen. Puede hacerlo almacenando la propiedad en el archivo de proyecto.

 El primer paso para conservar una propiedad en un archivo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proyecto es obtener la jerarquía del proyecto como una interfaz. Puede obtener esta interfaz mediante Automation <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>o mediante . Una vez obtenida la interfaz, puede usarla para determinar qué elemento de proyecto está seleccionado actualmente. Una vez que tenga el identificador <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> de elemento de proyecto, puede usar para agregar la propiedad.

 En los procedimientos siguientes, `Author` se conserva `Tom` la propiedad *VsPkg.cs* con el valor del archivo de proyecto.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Para obtener la jerarquía del proyecto con el objeto DTE

1. Agregue el código siguiente al VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Para conservar la propiedad de elemento de proyecto con el objeto DTE

1. Agregue el código siguiente al código especificado en el método del procedimiento anterior:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Para obtener la jerarquía del proyecto mediante IVsMonitorSelection

1. Agregue el código siguiente al VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Para conservar la propiedad de elemento de proyecto seleccionada, dada la jerarquía del proyecto

1. Agregue el código siguiente al código especificado en el método del procedimiento anterior:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Para comprobar que la propiedad se conserva

1. Inicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, abra o cree una solución.

2. Seleccione el elemento de proyecto VsPkg.cs en el **Explorador de soluciones**.

3. Use un punto de interrupción o determine de otro modo que el VSPackage está cargado y que SetItemAttribute se ejecuta.

   > [!NOTE]
   > Puede cargar automáticamente un VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>en el contexto de la interfaz de usuario. Para obtener más información, vea [Cargar VSPackages](../extensibility/loading-vspackages.md).

4. Cierre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, abra el archivo de proyecto en el Bloc de notas. Debería ver \<la etiqueta Author> con el valor Tom, como se indica a continuación:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Vea también

- [Herramientas personalizadas](../extensibility/internals/custom-tools.md)

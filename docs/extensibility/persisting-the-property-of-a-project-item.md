---
title: Conservar la propiedad de un elemento de proyecto | Microsoft Docs
description: Obtenga información sobre cómo conservar una propiedad que se agrega a un elemento de proyecto almacenando la propiedad en el archivo de proyecto en el tipo de proyecto extendido.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72de98e08581b105322b07390d85b95c06b1083c
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862695"
---
# <a name="persist-the-property-of-a-project-item"></a>Conservar la propiedad de un elemento de proyecto
Es posible que desee conservar una propiedad agregada a un elemento de proyecto, como el autor de un archivo de código fuente. Puede hacerlo almacenando la propiedad en el archivo de proyecto.

 El primer paso para conservar una propiedad en un archivo de proyecto es obtener la jerarquía del proyecto como una <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz. Puede obtener esta interfaz mediante la automatización o mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Una vez obtenida la interfaz, puede usarla para determinar qué elemento de proyecto está seleccionado actualmente. Una vez que tenga el identificador del elemento de proyecto, puede utilizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> para agregar la propiedad.

 En los procedimientos siguientes, se conserva la  propiedad VsPkg.CS `Author` con el valor del `Tom` archivo de proyecto.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Para obtener la jerarquía del proyecto con el objeto DTE

1. Agregue el código siguiente a su VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Para conservar la propiedad del elemento de proyecto con el objeto DTE

1. Agregue el código siguiente al código proporcionado en el método en el procedimiento anterior:

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

1. Agregue el código siguiente a su VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

1. Agregue el código siguiente al código proporcionado en el método en el procedimiento anterior:

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

2. Seleccione el elemento de proyecto VsPkg.cs en **Explorador de soluciones**.

3. Use un punto de interrupción o, de lo contrario, determine que el VSPackage está cargado y que SetItemAttribute se ejecuta.

   > [!NOTE]
   > Puede cargar automáticamente un VSPackage en el contexto de la interfaz de usuario <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Para obtener más información, vea [cargar VSPackages](../extensibility/loading-vspackages.md).

4. Cierre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, abra el archivo de proyecto en el Bloc de notas. Debería ver la \<Author> etiqueta con el valor Tom, como se indica a continuación:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Consulte también

- [Herramientas personalizadas](../extensibility/internals/custom-tools.md)

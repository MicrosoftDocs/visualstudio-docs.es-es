---
title: Extender el filtro de Explorador de soluciones | Microsoft Docs
description: Obtenga información acerca de cómo extender la funcionalidad de filtro de Explorador de soluciones para mostrar u ocultar distintos archivos en el SDK de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cde3377582c3bac0c27371e25f28e5151d641db1
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994568"
---
# <a name="extend-the-solution-explorer-filter"></a>Extender el filtro de Explorador de soluciones
Puede extender **Explorador de soluciones** funcionalidad de filtro para mostrar u ocultar distintos archivos. Por ejemplo, puede crear un filtro que muestre solo los archivos de generador de clases de C# en el **Explorador de soluciones**, como se muestra en este tutorial.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Crear un proyecto de paquete de Visual Studio

1. Cree un proyecto VSIX denominado `FileFilter` . Agregue una plantilla de elemento de comando personalizada denominada **FileFilter**. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Agregue una referencia a `System.ComponentModel.Composition` y `Microsoft.VisualStudio.Utilities` .

3. Haga que el comando de menú aparezca en la barra de herramientas **Explorador de soluciones** . Abra el archivo *FileFilterPackage. Vsct* .

4. Cambie el `<Button>` bloque a lo siguiente:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Actualización del archivo de manifiesto

1. En el archivo *source. Extension. vsixmanifest* , agregue un recurso que sea un componente de MEF.

2. En la pestaña **activos** , elija el botón **nuevo** .

3. En el campo **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

4. En el campo **origen** , elija **un proyecto en la solución actual**.

5. En el campo **proyecto** , elija **FileFilter** y elija el botón **Aceptar** .

### <a name="add-the-filter-code"></a>Agregar el código de filtro

1. Agregue algunos GUID al archivo *FileFilterPackageGuids.CS* :

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Agregue un archivo de clase al proyecto FileFilter denominado *FileNameFilter.CS*.

3. Reemplace el espacio de nombres vacío y la clase vacía por el código siguiente.

     El `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` método toma la colección que contiene la raíz de la solución ( `rootItems` ) y devuelve la colección de elementos que se van a incluir en el filtro.

     El `ShouldIncludeInFilter` método filtra los elementos de la jerarquía de **Explorador de soluciones** en función de la condición especificada.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. En *FileFilter.CS*, quite la colocación del comando y el código de control del constructor FileFilter. El resultado debería ser similar al siguiente:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Quite `ShowMessageBox()` también el método.

5. En *FileFilterPackage.CS*, reemplace el código del `Initialize()` método por lo siguiente:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Prueba del código

1. Compile y ejecute el proyecto. Se muestra una segunda instancia de Visual Studio. Esto se denomina instancia experimental.

2. En la instancia experimental de Visual Studio, abra un proyecto de C#.

3. Busque el botón que agregó en la barra de herramientas **Explorador de soluciones** . Debe ser el cuarto botón de la izquierda.

4. Al hacer clic en el botón, se deben filtrar todos los archivos y verá que todos los **elementos se han filtrado de la vista.** en el **Explorador de soluciones**.

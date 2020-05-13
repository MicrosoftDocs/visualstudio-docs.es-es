---
title: Ampliación del filtro del Explorador de soluciones ( Solución Explorer) Microsoft Docs
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
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711571"
---
# <a name="extend-the-solution-explorer-filter"></a>Extienda el filtro del Explorador de soluciones
Puede ampliar la funcionalidad de filtro **del Explorador** de soluciones para mostrar u ocultar diferentes archivos. Por ejemplo, puede crear un filtro que muestre solo los archivos de fábrica de clases de C- en el **Explorador**de soluciones , como se muestra en este tutorial.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

### <a name="create-a-visual-studio-package-project"></a>Crear un proyecto de paquete de Visual Studio

1. Cree un proyecto `FileFilter`VSIX denominado . Agregue una plantilla de elemento de comando personalizada denominada **FileFilter**. Para obtener más información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Agregue una `System.ComponentModel.Composition` referencia `Microsoft.VisualStudio.Utilities`a y .

3. Haga que el comando de menú aparezca en la barra de herramientas del Explorador de **soluciones.** Abra el archivo *FileFilterPackage.vsct.*

4. Cambie `<Button>` el bloque a lo siguiente:

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

1. En el archivo *source.extension.vsixmanifest,* agregue un recurso que sea un componente MEF.

2. En la pestaña **Assets(Assets),** elija el botón **New (Nuevo).**

3. En el campo **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.

4. En el campo **Origen,** elija Un proyecto en la **solución actual.**

5. En el campo **Proyecto,** elija **FileFilter**y, a continuación, elija el botón **Aceptar.**

### <a name="add-the-filter-code"></a>Agregue el código de filtro

1. Agregue algunos GUID al archivo *FileFilterPackageGuids.cs:*

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Agregue un archivo de clase al proyecto FileFilter denominado *FileNameFilter.cs*.

3. Reemplace el espacio de nombres vacío y la clase vacía por el código siguiente.

     El `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` método toma la colección que`rootItems`contiene la raíz de la solución ( ) y devuelve la colección de elementos que se incluirán en el filtro.

     El `ShouldIncludeInFilter` método filtra los elementos de la jerarquía del **Explorador** de soluciones en función de la condición que especifique.

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

4. En *FileFilter.cs*, quite el código de ubicación y control de comandos del constructor FileFilter. El resultado debería tener este aspecto:

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

     Elimine `ShowMessageBox()` el método también.

5. En *FileFilterPackage.cs*, reemplace `Initialize()` el código del método por el siguiente:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Prueba del código

1. Compile y ejecute el proyecto. Se muestra una segunda instancia de Visual Studio. Esto se denomina instancia experimental.

2. En la instancia experimental de Visual Studio, abra un proyecto de C.

3. Busque el botón que agregó en la barra de herramientas del Explorador de **soluciones.** Debe ser el cuarto botón de la izquierda.

4. Al hacer clic en el botón, todos los archivos deben filtrarse y debería ver **todos los elementos se han filtrado de** la vista. en el **Explorador de soluciones**.

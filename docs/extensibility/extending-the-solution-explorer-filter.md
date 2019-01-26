---
title: Ampliar el filtro del explorador de soluciones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ef616473b2164d3fce6659c9db925deba2f50ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921175"
---
# <a name="extend-the-solution-explorer-filter"></a>Ampliar el filtro del explorador de soluciones
Puede extender **el Explorador de soluciones** filtrar funcionalidad para mostrar u ocultar archivos diferentes. Por ejemplo, puede crear un filtro que solo clase factory archivos de C# se muestra el **el Explorador de soluciones**, tal y como se muestra en este tutorial.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Crear un proyecto de paquete de Visual Studio  
  
1.  Cree un proyecto VSIX denominado `FileFilter`. Agregar una plantilla de elemento de comando personalizado denominada **FileFilter**. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Agregue una referencia a `System.ComponentModel.Composition` y `Microsoft.VisualStudio.Utilities`.  
  
3.  Hacer que el comando de menú aparezca en el **el Explorador de soluciones** barra de herramientas. Abra el *FileFilterPackage.vsct* archivo.  
  
4.  Cambiar el `<Button>` bloque al siguiente:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Actualizar el archivo de manifiesto  
  
1.  En el *source.extension.vsixmanifest* , agregue un recurso que es un componente MEF.  
  
2.  En el **activos** ficha, elija la **New** botón.  
  
3.  En el **tipo** seleccione **Microsoft.VisualStudio.MefComponent**.  
  
4.  En el **origen** seleccione **un proyecto de la solución actual**.  
  
5.  En el **proyecto** seleccione **FileFilter**y, a continuación, elija el **Aceptar** botón.  
  
### <a name="add-the-filter-code"></a>Agregue el código de filtro  
  
1.  Agregar algún GUID para el *FileFilterPackageGuids.cs* archivo:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Agregar un archivo de clase al proyecto FileFilter denominado *FileNameFilter.cs*.  
  
3.  Reemplace el espacio de nombres vacío y la clase vacía con el código siguiente.  
  
     El `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` método toma la colección que contiene la raíz de la solución (`rootItems`) y devuelve la colección de elementos que se incluirán en el filtro.  
  
     El `ShouldIncludeInFilter` método filtra los elementos en el **el Explorador de soluciones** jerarquía basada en la condición de que especifique.  
  
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
  
4.  En *FileFilter.cs*, quite la selección de ubicación de comando y control de código desde el constructor FileFilter. El resultado debería tener este aspecto:  
  
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
  
     Quitar el `ShowMessageBox()` método así.  
  
5.  En *FileFilterPackage.cs*, reemplace el código en el `Initialize()` método con lo siguiente:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Probar el código  
  
1.  Compile y ejecute el proyecto. Se muestra una segunda instancia de Visual Studio. Esto se denomina la instancia experimental.  
  
2.  En la instancia experimental de Visual Studio, abra un proyecto de C#.  
  
3.  Busque el botón que agregó en el **el Explorador de soluciones** barra de herramientas. Debe ser el cuarto botón desde la izquierda.  
  
4.  Cuando haga clic en el botón, se deben filtrar todos los archivos y debería ver **todos los elementos se han filtrado de la vista.** en el **el Explorador de soluciones**.
---
title: "Extender el filtro del explorador de soluciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Explorador de soluciones, extender"
  - "extensibilidad [Visual Studio], proyectos y soluciones"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Extender el filtro del explorador de soluciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede extender **el Explorador de soluciones** funcionalidad para mostrar u ocultar diferentes archivos de filtro. Por ejemplo, puede crear un filtro que muestre sólo archivos C\# clase factory en el **el Explorador de soluciones**, como se muestra en este tutorial.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Crear un proyecto de paquete de Visual Studio  
  
1.  Cree un proyecto VSIX denominado `FileFilter`. Agregar una plantilla de elemento de comando personalizado denominada **FileFilter**. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Agregue una referencia a `System.ComponentModel.Composition` y `Microsoft.VisualStudio.Utilities`.  
  
3.  Hacer que el comando de menú aparezca en el **el Explorador de soluciones** barra de herramientas. Abra el archivo FileFilterPackage.vsct.  
  
4.  Cambiar el `<Button>` Bloquear a la siguiente:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### Actualizar el archivo de manifiesto  
  
1.  En el archivo source.extension.vsixmanifest, agregar un recurso que es un componente MEF.  
  
2.  En la pestaña **Activos**, elija el botón **Nuevo**.  
  
3.  En el **tipo** a continuación, elija **Microsoft.VisualStudio.MefComponent**.  
  
4.  En el **origen** a continuación, elija **un proyecto de la solución actual**.  
  
5.  En el **proyecto** a continuación, elija **FileFilter**, y, a continuación, elija la **Aceptar** botón.  
  
### Agregue el código de filtro  
  
1.  Agregue algunos GUID en el archivo FileFilterPackageGuids.cs:  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Agregue un archivo de clase al proyecto FileFilter denominado FileNameFilter.cs.  
  
3.  Reemplace el espacio de nombres vacío y la clase vacía con el código siguiente.  
  
     El `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` método toma la colección que contiene la raíz de la solución \(`rootItems`\) y devuelve la colección de elementos que se incluirán en el filtro.  
  
     El `ShouldIncludeInFilter` método filtra los elementos de la **el Explorador de soluciones** jerarquía basada en la condición de que especifique.  
  
    ```c#  
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
  
4.  En FileFilter.cs, quite el código de ubicación y el control de comando del constructor FileFilter. El resultado debería tener este aspecto:  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Quite también el método ShowMessageBox\(\).  
  
5.  En FileFilterPackage, cs, reemplace el código en el método Initialize\(\) con lo siguiente:  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### Probar el código  
  
1.  Compile y ejecute el proyecto. Aparece una segunda instancia de Visual Studio. Esto se denomina la instancia experimental.  
  
2.  En la instancia experimental de Visual Studio, abra un proyecto de C\#.  
  
3.  Busque el botón que agregar en la barra de herramientas del explorador de soluciones. Debe ser el cuarto botón desde la izquierda.  
  
4.  Al hacer clic en el botón, se deben filtrar todos los archivos, y debería ver "se han filtrado todos los elementos de la vista". en el Explorador de soluciones.
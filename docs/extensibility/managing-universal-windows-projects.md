---
title: Administración de proyectos universales de Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "81744939"
---
# <a name="manage-universal-windows-projects"></a>Administrar proyectos universales de Windows

Las aplicaciones universales de Windows son aplicaciones que tienen como destino Windows 8.1 y Windows Phone 8,1, lo que permite a los desarrolladores usar código y otros recursos en ambas plataformas. El código compartido y los recursos se mantienen en un proyecto compartido, mientras que el código y los recursos específicos de la plataforma se mantienen en proyectos independientes, uno para Windows y el otro para Windows Phone. Para obtener más información sobre las aplicaciones universales de Windows, consulte [aplicaciones universales de Windows](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Las extensiones de Visual Studio que administran proyectos deben tener en cuenta que los proyectos de aplicaciones universales de Windows tienen una estructura que difiere de las aplicaciones de una sola plataforma. En este tutorial se muestra cómo navegar por el proyecto compartido y administrar los elementos compartidos.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Navegar por el proyecto compartido

1. Cree un proyecto VSIX de C# denominado **TestUniversalProject**. (**Archivo**  >  **Nueva**  >  **Proyecto** y, **C#** a continuación,  >  **extensibilidad**de C#  >  **paquete de Visual Studio**). Agregue una plantilla de elemento de proyecto de **comando personalizado** (en el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**y, a continuación, vaya a **extensibilidad**). Asigne al archivo el nombre **TestUniversalProject**.

2. Agregue una referencia a *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* y *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (en la sección de **extensiones** ).

3. Abra *TestUniversalProject.CS* y agregue las siguientes `using` directivas:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. En la `TestUniversalProject` clase, agregue un campo privado que apunte a la ventana de **salida** .

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Establezca la referencia en el panel de salida dentro del constructor TestUniversalProject:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Quite el código existente del `ShowMessageBox` método:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Obtiene el objeto DTE, que se va a usar para varios propósitos diferentes en este tutorial. Además, asegúrese de que se carga una solución cuando se hace clic en el botón de menú.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Busque el proyecto compartido. El proyecto compartido es un contenedor puro; no genera ni genera salidas. El método siguiente busca el primer proyecto compartido en la solución buscando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto que tiene la capacidad de proyecto compartido.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. En el `ShowMessageBox` método, se genera el título (el nombre del proyecto que aparece en el **Explorador de soluciones**) del proyecto compartido.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Obtenga el proyecto de plataforma activa. Los proyectos de plataforma son los proyectos que contienen código y recursos específicos de la plataforma. El método siguiente usa el nuevo campo <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> para obtener el proyecto de plataforma activo.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. En el `ShowMessageBox` método, se genera el título del proyecto de plataforma activa.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Recorra en iteración los proyectos de la plataforma. El método siguiente obtiene todos los proyectos de importación (plataforma) del proyecto compartido.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Si el usuario ha abierto un proyecto de aplicación universal de Windows de C++ en la instancia experimental, el código anterior produce una excepción. Este es un problema conocido. Para evitar la excepción, reemplace el `foreach` bloque anterior por lo siguiente:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. En el `ShowMessageBox` método, se genera el título de cada proyecto de plataforma. Inserte el código siguiente después de la línea que genera el título del proyecto de plataforma activa. En esta lista solo aparecen los proyectos de plataforma que se cargan.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Cambiar el proyecto de plataforma activa. El siguiente método establece el proyecto activo mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. En el `ShowMessageBox` método, cambie el proyecto de plataforma activa. Inserte este código dentro del `foreach` bloque.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Pruébelo ahora. Presione F5 para iniciar la instancia experimental. Cree un proyecto de aplicación de Windows universal Hub en la instancia experimental (en el cuadro de diálogo **nuevo proyecto** , en **Visual C#**  >  **Windows**  >  **Windows 8**  >  **universal**  >  **Hub App**). Una vez cargada la solución, vaya al menú **herramientas** y haga clic en **invocar TestUniversalProject**y, a continuación, compruebe el texto en el panel de **salida** . Debe ver algo parecido a lo siguiente:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Administrar los elementos compartidos en el proyecto de plataforma

1. Busque los elementos compartidos en el proyecto de plataforma. Los elementos del proyecto compartido aparecen en el proyecto de plataforma como elementos compartidos. No puede verlos en el **Explorador de soluciones**, pero puede recorrer la jerarquía del proyecto para encontrarlos. El método siguiente recorre la jerarquía y recopila todos los elementos compartidos. Opcionalmente, genera el título de cada elemento,. Los elementos compartidos se identifican mediante la nueva propiedad <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. En el `ShowMessageBox` método, agregue el siguiente código para recorrer los elementos de la jerarquía del proyecto de plataforma. Insértelo dentro del `foreach` bloque.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Lea los elementos compartidos. Los elementos compartidos aparecen en el proyecto de plataforma como archivos vinculados ocultos y puede leer todas las propiedades como archivos vinculados ordinarios. En el código siguiente se lee la ruta de acceso completa del primer elemento compartido.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Pruébelo ahora. Presione **F5** para iniciar la instancia experimental. Cree un proyecto de aplicación de C# universal Hub en la instancia experimental (en el cuadro de diálogo **nuevo proyecto** , **Visual C#**  >  **Windows**  >  **Windows 8**  >  **universal**  >  **Hub App**) vaya al menú **herramientas** , haga clic en **invocar TestUniversalProject**y, a continuación, compruebe el texto del panel de **salida** . Debe ver algo parecido a lo siguiente:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Detección de cambios en proyectos de plataforma y proyectos compartidos

1. Puede usar eventos de jerarquía y de proyecto para detectar cambios en proyectos compartidos, al igual que en los proyectos de plataforma. Sin embargo, los elementos de proyecto del proyecto compartido no están visibles, lo que significa que ciertos eventos no se activan cuando se modifican los elementos de proyecto compartidos.

    Tenga en cuenta la secuencia de eventos cuando se cambia el nombre de un archivo en un proyecto:

   1. El nombre de archivo se cambia en el disco.

   2. El archivo de proyecto se actualiza para incluir el nuevo nombre del archivo.

      Los eventos de la jerarquía (por ejemplo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> ) suelen realizar un seguimiento de los cambios mostrados en la interfaz de usuario, como en el **Explorador de soluciones**. Los eventos de jerarquía consideran que una operación de cambio de nombre de archivo se compone de una eliminación de archivos y, a continuación, un archivo adicional. Sin embargo, cuando se cambian los elementos invisibles, el sistema de eventos de la jerarquía activa un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento pero no un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento. Por lo tanto, si cambia el nombre de un archivo en un proyecto de plataforma, obtendrá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> , pero si cambia el nombre de un archivo en un proyecto compartido, solo obtendrá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .

      Para realizar el seguimiento de los cambios en los elementos de proyecto, puede controlar los eventos del elemento de proyecto DTE (los que se encuentran en <xref:EnvDTE.ProjectItemsEventsClass> ). Sin embargo, si está controlando un gran número de eventos, puede obtener un mejor rendimiento al controlar los eventos en <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . En este tutorial se muestran solo los eventos de la jerarquía y los eventos DTE. En este procedimiento, agregará un agente de escucha de eventos a un proyecto compartido y un proyecto de plataforma. Después, al cambiar el nombre de un archivo en un proyecto compartido y en otro archivo en un proyecto de plataforma, puede ver los eventos que se desencadenan para cada operación de cambio de nombre.

      En este procedimiento, agregará un agente de escucha de eventos a un proyecto compartido y un proyecto de plataforma. Después, al cambiar el nombre de un archivo en un proyecto compartido y en otro archivo en un proyecto de plataforma, puede ver los eventos que se desencadenan para cada operación de cambio de nombre.

2. Agregue un agente de escucha de eventos. Agregue un nuevo archivo de clase al proyecto y llámelo *HierarchyEventListener.CS*.

3. Abra el archivo *HierarchyEventListener.CS* y agregue las siguientes directivas Using:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. `HierarchyEventListener`Implemente la clase <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implemente los miembros de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , como en el código siguiente.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. En la misma clase, agregue otro controlador de eventos para el evento DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> , que tiene lugar siempre que se cambia el nombre de un elemento de proyecto.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Suscríbase a los eventos de la jerarquía. Debe registrarse por separado para cada proyecto del que esté realizando el seguimiento. Agregue el código siguiente en `ShowMessageBox` , uno para el proyecto compartido y el otro para uno de los proyectos de la plataforma.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Regístrese en el evento de elemento de proyecto DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . Agregue el código siguiente después de enlazar el segundo agente de escucha.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modifique el elemento compartido. No se pueden modificar elementos compartidos en un proyecto de plataforma; en su lugar, debe modificarlos en el proyecto compartido que sea el propietario real de estos elementos. Puede obtener el identificador de elemento correspondiente en el proyecto compartido con <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> , lo que le proporciona la ruta de acceso completa del elemento compartido. Después, puede modificar el elemento compartido. El cambio se propaga a los proyectos de la plataforma.

    > [!IMPORTANT]
    > Debe averiguar si un elemento de proyecto es un elemento compartido antes de modificarlo.

     El método siguiente modifica el nombre de un archivo de elemento de proyecto.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Llame a este método después de todo el resto del código de `ShowMessageBox` para modificar el nombre de archivo del elemento en el proyecto compartido. Inserte esto después del código que obtiene la ruta de acceso completa del elemento en el proyecto compartido.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Compile y ejecute el proyecto. Cree una aplicación de C# universal Hub en la instancia experimental, vaya al menú **herramientas** y haga clic en **invocar TestUniversalProject**y compruebe el texto en el panel de salida general. El nombre del primer elemento del proyecto compartido (esperamos que sea el archivo *app. Xaml* ) debe cambiarse y debería ver que se <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> ha desencadenado el evento. En este caso, puesto que el cambio de nombre de *app. Xaml* hace que también se cambie el nombre de *app.Xaml.CS* , debería ver cuatro eventos (dos para cada proyecto de plataforma). (Los eventos DTE no realizan el seguimiento de los elementos del proyecto compartido). Debería ver dos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventos (uno para cada uno de los proyectos de plataforma), pero no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> los eventos.

12. Ahora intente cambiar el nombre de un archivo en un proyecto de plataforma y puede ver la diferencia en los eventos que se desencadenan. Agregue el código siguiente en `ShowMessageBox` después de la llamada a `ModifyFileName` .

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Compile y ejecute el proyecto. Cree un proyecto universal de C# en la instancia experimental, vaya al menú **herramientas** y haga clic en **invocar TestUniversalProject**y compruebe el texto en el panel de salida general. Después de cambiar el nombre del archivo en el proyecto de plataforma, debería ver un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento y un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento. Puesto que no se ha podido cambiar el archivo porque no se propagan otros archivos y, como los cambios en los elementos de un proyecto de plataforma, no se propagan en ningún lugar, solo hay uno de estos eventos.

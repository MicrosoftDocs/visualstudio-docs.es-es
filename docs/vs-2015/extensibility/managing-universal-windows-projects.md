---
title: Administración de proyectos de Windows Universal | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2c10232b917e8343ace8d1a31fcd3609ecdfb95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783784"
---
# <a name="managing-universal-windows-projects"></a>Administración de proyectos de Windows universal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplicaciones universales de Windows son aplicaciones que tienen como destino Windows 8.1 y Windows Phone 8.1, lo que permite a los desarrolladores usar código y otros activos en ambas plataformas. El código compartido y los recursos se mantienen en un proyecto compartido, mientras que el código específico de plataforma y los recursos se mantienen en proyectos independientes, uno para Windows y otro para Windows Phone. Para obtener más información sobre las aplicaciones universales de Windows, consulte [aplicaciones universales de Windows](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Extensiones de Visual Studio que administran proyectos deben ser consciente de que los proyectos de aplicaciones universales de Windows tienen una estructura que difiere de las aplicaciones de plataforma única. En este tutorial se muestra cómo navegar por el proyecto compartido y administrar los elementos compartidos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Navegar por el proyecto compartido  
  
1.  Cree un proyecto de VSIX de C# denominado **TestUniversalProject**. (**Archivo, nuevo, proyecto** y, a continuación, **el paquete de Visual Studio C#, extensibilidad,**). Agregar un **comando personalizado** plantilla de elemento de proyecto (en el Explorador de soluciones, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**, a continuación, vaya a **extensibilidad**). Nombre del archivo **TestUniversalProject**.  
  
2.  Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll y Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (en el **extensiones** sección).  
  
3.  Abra TestUniversalProject.cs y agregue el siguiente `using` instrucciones:  
  
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
  
4.  En la clase TestUniversalProject, agregue un campo privado que apunta a la **salida** ventana.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Establezca la referencia en el panel de salida dentro de TestUniversalProject constructor:  
  
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
  
6.  Quite el código existente desde el `ShowMessageBox` método:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Obtener el objeto DTE, que se usarán para propósitos diferentes en este tutorial. Además, asegúrese de que se carga una solución cuando se hace clic en el botón de menú.  
  
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
  
8.  Busque el proyecto compartido. El proyecto compartido es un contenedor puro; No cree ni generar salidas. El método siguiente busca el primer proyecto compartido en la solución mediante la búsqueda de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto que tiene la capacidad de proyecto compartido.  
  
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
  
9. En el `ShowMessageBox` método, el título de salida (el nombre del proyecto que aparece en el **el Explorador de soluciones**) del proyecto compartido.  
  
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
  
10. Obtenga el proyecto de la plataforma activa. Los proyectos de plataforma son los proyectos que contienen recursos y código específico de plataforma. El método siguiente utiliza el nuevo campo <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> para que el proyecto de la plataforma activa.  
  
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
  
11. En el `ShowMessageBox` de salida de método, el título del proyecto de la plataforma activa.  
  
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
  
12. Recorrer en iteración los proyectos de plataforma. El siguiente método obtiene todos los proyectos (plataforma) importar desde el proyecto compartido.  
  
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
    >  Si el usuario ha abierto un proyecto de aplicación de C++ universal Windows en la instancia experimental, el código anterior produce una excepción. Se trata de un problema conocido. Para evitar la excepción, reemplace el `foreach` bloquear arriba con lo siguiente:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. En el `ShowMessageBox` método, el título de cada proyecto de la plataforma de salida. Inserte el código siguiente después de la línea que genera el título del proyecto de la plataforma activa. Solo los proyectos de plataforma que se cargan aparecen en esta lista.  
  
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
  
14. Cambie el proyecto de la plataforma activa. El método siguiente establece el proyecto activo mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. En el `ShowMessageBox` método, cambie el proyecto de la plataforma activa. Inserte este código dentro de la `foreach` bloque.  
  
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
  
16. Ahora, pruébela. Presione F5 para iniciar la instancia experimental. Crear un proyecto de aplicación universal de concentrador de C# en la instancia experimental (en el **nuevo proyecto** cuadro de diálogo, **Visual C# / Windows / Windows 8 / Universal / aplicación Hub**). Una vez que se carga la solución, vaya a la **herramientas** menú y haga clic en **invocar TestUniversalProject**y, a continuación, compruebe el texto el **salida** panel. Debería ver algo parecido a lo siguiente:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Administrar los elementos compartidos en el proyecto de plataforma  
  
1.  Buscar los elementos compartidos en el proyecto de plataforma. Los elementos en el proyecto compartido aparecen en el proyecto de plataforma como los elementos compartidos. No puede verlas en la **el Explorador de soluciones**, pero puede recorrer la jerarquía del proyecto para encontrarlos. El siguiente método recorre a la jerarquía y recopila todos los elementos compartidos. Genera el título de cada elemento, si lo desea. Los elementos compartidos se identifican mediante la nueva propiedad <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
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
  
2.  En el `ShowMessageBox` método, agregue el siguiente código para recorrer los elementos de jerarquía del proyecto de plataforma. Insertar en el interior del `foreach` bloque.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Leer los elementos compartidos. Los elementos compartidos aparecen en el proyecto de plataforma como los archivos vinculados ocultos, y puede leer todas las propiedades como los archivos vinculados normales. El siguiente código lee la ruta de acceso completa del primer elemento compartido.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Ahora, pruébela. Presione F5 para iniciar la instancia experimental. Crear un proyecto de aplicación universal de concentrador de C# en la instancia experimental (en el **nuevo proyecto** cuadro de diálogo, **Visual C# / Windows / Windows 8 / Universal / aplicación Hub**) vaya a la **herramientas** menú y haga clic en **invocar TestUniversalProject**y, a continuación, compruebe el texto el **salida** panel. Debería ver algo parecido a lo siguiente:  
  
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
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Detectar cambios en los proyectos de plataforma y los proyectos compartidos  
  
1. Puede usar eventos de jerarquía y el proyecto para detectar cambios en los proyectos compartidos, se puede hacer para proyectos de la plataforma. Sin embargo, los elementos de proyecto en el proyecto compartido no son visibles, lo que significa que algunos eventos no se activan cuando se cambian los elementos de proyecto compartido.  
  
    Tenga en cuenta la secuencia de eventos cuando se cambia el nombre de un archivo en un proyecto:  
  
   1. Cambie el nombre de archivo en el disco.  
  
   2. El archivo de proyecto se actualiza para incluir el nuevo nombre del archivo.  
  
      Eventos de la jerarquía (por ejemplo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) suele realizar un seguimiento de los cambios que se muestran en la interfaz de usuario, como en el **el Explorador de soluciones**. Eventos de la jerarquía considere una operación de cambio de nombre de archivo que constan de una eliminación de archivos y, a continuación, la adición de un archivo. Sin embargo, cuando se modifican elementos invisibles, el sistema de eventos de la jerarquía activa una <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventos, pero no un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> eventos. Por lo tanto, si cambia el nombre de un archivo en un proyecto de la plataforma, obtendrá dos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, pero si cambia el nombre de un archivo en un proyecto compartido, solo obtendrá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
      Para realizar el seguimiento de cambios de elementos de proyecto, puede controlar eventos de elemento de proyecto DTE (los que se encuentra en <xref:EnvDTE.ProjectItemsEventsClass>). Sin embargo, si lo está manejando gran número de eventos, puede obtener un mejor rendimiento, controlar eventos en <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. En este tutorial se muestran solo los eventos de jerarquía y los eventos DTE. En este procedimiento agregará un agente de escucha de eventos para un proyecto compartido y un proyecto de la plataforma. A continuación, al cambiar el nombre de un archivo en un proyecto compartido y otro en un proyecto de la plataforma, puede ver los eventos que se activan para cada operación de cambio de nombre.  
  
      En este procedimiento agregará un agente de escucha de eventos para un proyecto compartido y un proyecto de la plataforma. A continuación, al cambiar el nombre de un archivo en un proyecto compartido y otro en un proyecto de la plataforma, puede ver los eventos que se activan para cada operación de cambio de nombre.  
  
2. Agregar un agente de escucha de eventos. Agregue un nuevo archivo de clase al proyecto y llámelo HierarchyEventListener.cs.  
  
3. Abra el archivo HierarchyEventListener.cs y agregue las siguientes instrucciones using:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  
  
   ```  
  
4. Tiene la `HierarchyEventListener` implementan <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  
  
   ```  
  
5. Implemente los miembros de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, como en el código siguiente.  
  
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
  
6. En la misma clase, agregue otro controlador de eventos para el evento DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, que se produce cuando se cambia el nombre de un elemento de proyecto.  
  
   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  
  
7. Regístrese para obtener los eventos de la jerarquía. Deberá registrarse por separado para cada proyecto que se está realizando el seguimiento. Agregue el código siguiente en `ShowMessageBox`, uno para el proyecto compartido y otro para uno de los proyectos de plataforma.  
  
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
  
8. Registrarse para el evento de elemento de proyecto DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Agregue el código siguiente después de enlazar el segundo agente de escucha.  
  
   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
   ```  
  
9. Modifique el elemento compartido. No se puede modificar los elementos compartidos en un proyecto de plataforma; en su lugar, debe modificar en el proyecto compartido que sea el propietario real de estos elementos. Puede obtener el identificador del elemento correspondiente en el proyecto compartido con <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, dándole la ruta de acceso completa del elemento compartido. A continuación, puede modificar el elemento compartido. El cambio se propaga a los proyectos de plataforma.  
  
    > [!IMPORTANT]
    >  Debe averiguar si un elemento de proyecto es un elemento compartido antes de modificarlo.  
  
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
  
10. Llame a este método después de todo el otro código en `ShowMessageBox` para modificar el archivo de nombre del elemento en el proyecto compartido. Inserte esto después del código que obtiene la ruta de acceso completa del elemento en el proyecto compartido.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Compile y ejecute el proyecto. Crear una aplicación de concentrador universal de C# en la instancia experimental, vaya a la **herramientas** menú y haga clic en **TestUniversalProject invocar**y compruebe el texto en el panel de resultados general. El nombre del primer elemento en el recurso compartido se debe cambiar el proyecto (se espera que esté el archivo App.xaml) y debería ver que el <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> ha desencadenado el evento. En este caso, ya que el cambio de nombre App.xaml produce App.xaml.cs se va a cambiar, así, debería ver cuatro eventos (dos para cada proyecto de plataforma). (Los eventos DTE no realizar seguimiento de los elementos en el proyecto compartido.) Debería ver dos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventos (una para cada uno de los proyectos de plataforma), pero no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> eventos.  
  
12. Ahora intente cambiar el nombre de un archivo en un proyecto de la plataforma, y puede ver la diferencia en los eventos que se desencadene. Agregue el código siguiente en `ShowMessageBox` después de llamar a `ModifyFileName`.  
  
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
  
13. Compile y ejecute el proyecto. Crear un proyecto Universal de C# en la instancia experimental, vaya a la **herramientas** menú y haga clic en **TestUniversalProject invocar**y compruebe el texto en el panel de resultados general. Una vez que se cambia el nombre del archivo en el proyecto de plataforma, debería ver un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> eventos y un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventos. Cambiando el archivo no produjo ningún otro archivo que se puede cambiar y, dado que los cambios realizados en elementos de un proyecto de plataforma no se propagan en cualquier lugar, hay sólo cada uno de estos eventos.


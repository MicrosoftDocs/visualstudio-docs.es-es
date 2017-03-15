---
title: "Carga de la solución ligera (LSL) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>Carga de la solución ligera (LSL)

## <a name="background-information-on-lsl"></a>Información general sobre LSL

Carga ligera de solución es una nueva característica de 2017 frente a lo que reducirá significativamente el tiempo de carga de la solución, lo que le permite ser más productivos rápidamente. Cuando se habilita LSL, Visual Studio no totalmente cargar proyectos hasta que comience a trabajar con ellos.

LSL puede afectar a las extensiones de Visual Studio. Extensiones cuyas características dependen de un proyecto que se va a cargar no funcionan o no funcionen correctamente sin seguir las instrucciones que se detallan en este documento.

Para obtener más información sobre LSL, use los siguientes vínculos:

* [Blog de carga de solución ligera](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* ¿Tiene preguntas? Póngase en contacto con nosotros en[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Habilitar la configuración de proyectos en modo "aplazado" de carga

1. Cierre cualquier solución abierta actualmente.
2. Vaya a **herramientas** > **opción** > **proyectos y soluciones** > **General** página de configuración.
3. Compruebe el **carga solución ligera** cuadro para habilitar la configuración.

Cuando se abre una solución con la configuración anterior activada, el IDE muestra una vista normal de los proyectos, pero no se cargan los proyectos.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Diferencias entre la carga aplazada y la carga normal de proyectos

Con una carga ligera soluciones, proyectos no se cargan cuando se abre una solución. Para estos "proyectos aplazados", se crea una jerarquía de código auxiliar. El Explorador de soluciones muestra la vista esperada con iconos y nombres de proyectos, no hay ninguna indicación de la interfaz de usuario que algunos o todos los proyectos que se encuentran en "modo diferido".

Con LSL habilitado, extensiones ya no pueden esperar que los proyectos necesarios ya están completamente se cargan cuando se desencadena una operación. Los llamadores necesitan comprobar si tienen una dependencia en los proyectos cargados. Si una extensión requiere información de un proyecto aplazado, la extensión, haga lo siguiente:

1. Cargar los proyectos según sea necesario.
2. Use la nueva **API de área de trabajo** para obtener información de un proyecto aplazado sin cargarlo.

El nuevo **API de área de trabajo** Permitir extensiones obtener información, como el proyecto propietario de un archivo de origen y todos los archivos de origen de un proyecto especificado, desde un proyecto aplazado. En algunos casos, sólo un conjunto limitado de proyectos necesitan cargarse. La opción adecuada es un equilibrio entre la frecuencia de las operaciones, la facilidad de enfoques alternativos y la experiencia general del usuario.

Todos los proyectos y carga de soluciones relacionadas con eventos todavía se activan en el modo LSL. Esto permite que componentes para obtener el comportamiento esperado de VS y se comportan de la misma manera que cuando se cargan los proyectos. La carga del proyecto relacionados con el trabajo realizado durante la solución abierta se redujo drásticamente aunque.

## <a name="ui-requirements-and-changes"></a>Cambios y los requisitos de la interfaz de usuario

Todos los de la interfaz de usuario debe tratar cargados y diferidos proyectos como iguales. Esto significa que cualquier acción que se puede realizar en un proyecto cargado debe ser aplicable a los proyectos diferidos, con algunas excepciones. Para ayudar a características de lograr esto, hay cambios en algunas API de plataforma existente, así como la introducción de nuevas API.

### <a name="expectations-for-ui"></a>Expectativas para la interfaz de usuario

1. Características deben mostrar que las diferencias no visual en función de si se cargan o se aplaza proyectos.
2. Cualquier lista o enumeración sobre proyectos de la solución cargada debe incluir proyectos aplazados.
3. Cualquier acción disponible en un proyecto cargado debe estar disponible en un proyecto aplazado.
4. Características debe proyectos de solicitud para cargar solo cuando:
  * No hay interacción directa del usuario con una característica. No cargue proyectos de forma preferente.
  * El usuario realiza un movimiento "Ver más resultados". Consulte a continuación esta directriz de la interfaz de usuario.
  * Solo el proyecto completamente cargado puede utilizarse para satisfacer la acción. Utilice LSL y API abiertas de proyecto siempre que sea posible y enviar la solicitud de característica pide cuando existe funcionalidad.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Cambios en la API para ayudar a impulsar la interfaz de usuario de la plataforma

1. Nuevas API se proporcionan para solicitar la solución si se abrió en modo de carga de la solución de ligero y cuántos proyectos están en un estado diferido.
2. Nuevo evento se proporciona para cuando se cargan todos los proyectos aplazados en la solución.
3. Nuevas API se proporcionan para pedir un proyecto si está aplazada.
4. Las API existentes se actualizan para incluir proyectos aplazados cuando se le soliciten para los proyectos cargados.
5. Las API existentes se actualizan para que expresa la solución se ha cargado completamente después de abre la solución.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Cómo agregar "Ver más resultados" para una característica.

Características que realizan una consulta en el contenido de proyectos deben considerar el impacto de proyectos aplazados. En algunas situaciones, características pueden obtener los resultados de la consulta de LSL y API de área de trabajo para un proyecto aplazado. En otros casos, las limitaciones de la característica requieren proyectos que se va a cargar. Ambas situaciones deben proporcionar un nuevo movimiento de "Ver más resultados" que permite a los usuarios cargar totalmente los proyectos y volver a consultar. Este movimiento habilita características ofrecer una mejor aproximación cuando hay proyectos aplazados al proporcionar al usuario una manera de obtener el resultado perfecto cuando se cargan realmente los proyectos.

Debe ser el algoritmo general de características:

### <a name="when-the-query-is-performed-over-a-single-project"></a>Cuando la consulta se realiza a través de un solo proyecto

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Cuando se realiza la consulta sobre la solución completa

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>Cambios en la API

### <a name="new-api"></a>Nueva API

IVsSolution7.IsSolutionLoadDeferred (out bool diferida)

Devuelve true si la solución actual se ha cargado en modo diferido. Tenga en cuenta que si la solución se cargó inicialmente en modo diferido, incluso si todos los proyectos aplazados finalmente había cargado en la sesión actual (deba a los gestos del usuario explícita o forzada por operaciones), esta propiedad seguiría devolviendo true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Devuelve el número de proyectos actualmente en modo diferido. Esta propiedad tendrá un valor en el intervalo [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Devuelve true si una jerarquía de proyectos se encuentra en estado de carga aplazada.

__VSENUMPROJFLAGS3 con los valores EPF_DEFERRED y EPF_NOTDEFERRED

Estos indicadores se pueden pasar a [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) para iterar sobre proyectos aplazados y diferida no.

### <a name="new-events"></a>Nuevos eventos

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Este evento se desencadena después de que se hayan cargado todos los proyectos aplazados. En este punto, VSPROPID_DeferredProjectCount es igual a 0. Observe que este evento no se genera como parte de la carga de la solución y no se producen en absoluto en una sesión. Sólo se activa cuando se cargan todos los proyectos aplazados.

### <a name="changes-to-existing-api"></a>Cambios en las API existente

* Pasar [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION a [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) devuelve aplazado proyectos.
* Pasar [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION no devuelve proyectos aplazados.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) se establece en true en la solución abierta. Proyectos diferidos se tratan como cargado de forma que este contexto se establece en gran parte anterior en modo de no LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount devuelve la suma de los proyectos cargados y diferidas.

## <a name="helpful-code-snippets"></a>Fragmentos de código útil

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Compruebe si se ha abierto una solución en modo de carga diferida

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Compruebe si se aplaza un proyecto

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Cargar proyecto

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Cargar un conjunto de proyectos

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Comprueba si la solución ha aplazado proyectos

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Obtener información detallada con las API de área de trabajo

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Cómo obtener información detallada sobre una solución LSL

Nuevas API de área de trabajo se exponen a través de IVsSolutionWorkspaceService para ayudar a recuperar información detallada sobre una solución.

Estas API se pueden utilizar para obtener el área de trabajo actual, la solución activa, la información de línea de comandos administrados, así como el servicio de índice para el área de trabajo. Estas API pueden aprovechar aún más el servicio de índice para obtener datos detallados, por ejemplo, todos los archivos de código fuente en un proyecto, el proyecto propietario de un archivo de origen, todos los proyectos incluidos en la solución actual, todas las referencias de P2P en un proyecto, etcetera.

Fragmentos de código siguientes muestran el uso de las API de área de trabajo.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Obtener IVsSolutionWorkspaceService inicialmente

>**Nota:** sólo obtenga IVsSolutionWorkspaceService en escenarios LSL para evitar que se cargue el paquete de la API de área de trabajo.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Nota:** los fragmentos de código siguientes se suponen _solutionWorkspaceService diferida ya está inicializado.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Obtener la información de línea de comandos administrada para aplazada proyectos para la configuración de soluciones activas

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Obtenga el archivo de solución activa LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Obtener el proyecto propietario de un archivo de código fuente

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Obtener todos los archivos de origen de un proyecto

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Obtener las referencias de P2P en un proyecto

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Obtener todos los proyectos en una solución

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Solución de problemas

Debido a la naturaleza de LSL, es intencional que los usuarios no pueden ver una diferencia entre los proyectos cargados y diferidas. Esto puede dificultar pruebas y desarrollo de características.

Puede habilitar las sugerencias visuales en la interfaz de usuario para proyectos aplazados haciendo lo siguiente:

1. Cierre Visual Studio.
2. Regedit.exe
3. Seleccione HKLM
4. Archivo > Cargar subárbol
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Escriba "VisualStudio" como un nombre de clave
7. Establezca `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Seleccione HKLM\VisualStudio
9. Archivo > Descargar subárbol
10. Inicie Visual Studio

Si tiene alguna pregunta adicional, póngase en contacto con [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).








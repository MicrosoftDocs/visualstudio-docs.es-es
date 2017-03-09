---
title: "C&#243;mo: Agregar o quitar referencias usando el Administrador de referencias | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ReferenceManager"
helpviewer_keywords: 
  - "ensamblados [Visual Studio], referencias"
  - "referencias del proyecto, agregar"
  - "referencias del proyecto, quitar"
  - "referencias [Visual Studio], agregar"
  - "referencias [Visual Studio], quitar"
  - "hacer referencia a ensamblados"
  - "hacer referencia a componentes, agregar referencias"
  - "hacer referencia a componentes, ensamblados no enumerados"
  - "hacer referencia a componentes, quitar referencias"
  - "proyectos de Visual Basic, referencias"
  - "proyectos de Visual C#, referencias"
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 45
caps.handback.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Agregar o quitar referencias usando el Administrador de referencias
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar el cuadro de diálogo **Administrador de referencias** para agregar y administrar referencias a componentes que usted, Microsoft u otra compañía hayan desarrollado.  Si va a desarrollar una aplicación de Windows universal, el proyecto hará referencia automáticamente a todos los archivos DLL correctos del SDK de Windows.  Si va a desarrollar una aplicación .NET, el proyecto hará referencia automáticamente a mscorlib.dll.  Algunas API de .NET se exponen en los componentes que debe agregar manualmente.  Las referencia a los componentes COM o a los componentes personalizados tienen que agregarse manualmente.  
  
## Agregar y quitar una referencia  
  
#### Para agregar una referencia  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo Referencias y elija **Agregar referencia**.  
  
2.  Especifique las referencias que desea agregar y elija el botón **Aceptar**.  
  
 Se abre el **Administrador de referencias** y se muestran las referencias disponibles por grupo.  El tipo de proyecto determina cuál de los grupos siguientes aparece:  
  
-   Ensamblados, con los subgrupos .NET Framework y Extensiones.  
  
-   Solución, con el subgrupo Proyectos.  
  
-   Windows, con los subgrupos Principal y Extensiones.  Puede explorar las referencias en el Kit de desarrollo de software de Windows \(Windows SDK\) o en los SDK de extensiones mediante el **Examinador de objetos**.  
  
-   Examinar, con el subgrupo Recientes.  
  
## Pestaña Ensamblados  
 En la pestaña **Ensamblados** se muestran todos los ensamblados de .NET Framework a los que se puede hacer referencia.  La pestaña **Ensamblados** no muestra ningún ensamblado de la caché global de ensamblados \(GAC\) porque los ensamblados de la GAC forman parte del entorno en tiempo de ejecución.  Si implementa o copia una aplicación que contiene una referencia a un ensamblado registrado en la memoria caché global de ensamblados, el ensamblado no se implementará ni copiará con la aplicación, independientemente de la configuración de Copia local.  Para obtener más información, consulte [Referencias de proyectos](http://go.microsoft.com/fwlink/?LinkId=238512).  
  
 Al agregar manualmente una referencia a cualquiera de los espacios de nombres EnvDTE \(EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a o EnvDTE100\), establezca la propiedad Incrustar tipos de interoperabilidad de la referencia en False en la ventana Propiedades.  Si establece esta propiedad en True, se pueden producir problemas de compilación debido a ciertas propiedades EnvDTE que no se pueden insertar.  
  
 Todos los proyectos de escritorio contienen una referencia implícita a mscorlib.  Los proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] contienen una referencia implícita a Microsoft.VisualBasic.  En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], todos los proyectos contienen una referencia implícita a System.Core, aunque se quite de la lista de referencias.  
  
 Si un tipo de proyecto no admite ensamblados, la pestaña no aparecerá en el cuadro de diálogo **Administrador de referencias**.  
  
 La pestaña Ensamblados consta de dos subpestañas:  
  
1.  .NET Framework muestra todos los ensamblados que conforman la versión de .NET Framework de destino.  
  
    -   Los ensamblados anunciados están en la versión completa de .NET Framework y se muestran en la lista .NET Framework cuando el proyecto tiene como destino un perfil de la versión de .NET Framework de destino.  Los ensamblados anunciados son grises para diferenciarlos de los ensamblados que existen en el perfil de proyecto de la versión de .NET Framework de destino.  Por ejemplo, si un proyecto tiene como destino .NET Framework 4 Client, en .NET Framework se muestran los ensamblados anunciados de .NET Framework 4.  Cuando un usuario agrega un ensamblado anunciado, se indica al usuario que, cuando cierre el cuadro de diálogo **Administrador de referencias**, la versión de destino del proyecto cambiará a .NET Framework 4 y se agregará al ensamblado anunciado.  
  
    -   Los proyectos de las aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] contienen referencias a todos los ensamblados de la versión de [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] de destino de forma predeterminada cuando se crea un proyecto.  En los proyectos administrados, un nodo de solo lectura bajo la carpeta Referencias del **Explorador de soluciones** indica la referencia a la versión completa de .NET Framework.  Por consiguiente, la pestaña .NET Framework no mostrará ninguno de los ensamblados de .NET Framework y en su lugar mostrará el siguiente mensaje: “Ya se hace referencia a todos los ensamblados de .NET Framework.  Use el Examinador de objetos para ver las referencias de .NET Framework”. Para los proyectos de escritorio, la pestaña .NET Framework muestra los ensamblados de la versión de .NET Framework de destino, y el usuario debe agregar las referencias que requiera la aplicación.  
  
2.  Las extensiones muestran todos los ensamblados que los proveedores externos de componentes y controles han desarrollado para ampliar la versión de .NET Framework de destino.  Dependiendo del propósito de la aplicación del usuario, puede que se necesiten estos ensamblados.  
  
    -   Las extensiones se rellenan con una enumeración de los ensamblados registrados en las ubicaciones siguientes:  
  
        ```  
        32-bit machine:  
        HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        64-bit machine:  
        HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        And older versions of the [Target Framework Identifier]  
        ```  
  
         Por ejemplo, si un proyecto tiene como destino .NET Framework 4 en un equipo de 32 bits, las extensiones muestran los ensamblados registrados en \\Microsoft\\.NETFramework\\v4.0\\AssemblyFoldersEx\\, \\Microsoft\\.NETFramework\\v3.5\\AssemblyFoldersEx\\, \\Microsoft\\.NETFramework\\v3.0\\AssemblyFoldersEx\\ y \\Microsoft\\.NETFramework\\v2.0\\AssemblyFoldersEx\\.  
  
 Dependiendo de la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] del proyecto, es posible que algunos componentes de la lista no aparezcan.  Esta desincronización puede aparecer bajo las condiciones siguientes:  
  
-   Un componente que utiliza una versión reciente de .NET Framework es incompatible con un proyecto que tiene como destino una versión anterior de .NET Framework.  
  
     Para obtener información sobre cómo cambiar la versión de destino de .NET Framework de un proyecto, vea [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
-   Un componente que utiliza [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] es incompatible con un proyecto que tiene como destino [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
     Al crear una nueva aplicación, algunos proyectos tienen como destino [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] de forma predeterminada.  Para obtener más información, vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
-   No se deben agregar referencias de archivos a resultados de otro proyecto de la misma solución, ya que puede provocar errores de compilación.  En lugar de hacerlo, use la ficha **Proyectos** del cuadro de diálogo **Agregar referencias** para crear referencias entre proyectos.  Esto facilita el trabajo en equipo, permitiendo una mejor administración de las bibliotecas de clases creadas en los proyectos.  Para obtener más información, vea [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md).  
  
-   > [!NOTE]
    >  En Visual Studio 2015, se crea una referencia de archivo en lugar de una referencia de proyecto si la versión de destino de .NET Framework de un proyecto es la 4.5 y la versión de .NET Framework de destino del otro proyecto es la 2, la 3, la 3.5 o la 4.0.  
  
#### Para mostrar un ensamblado en el cuadro de diálogo Agregar referencia  
  
-   Desplace o copie el ensamblado en una de las ubicaciones siguientes:  
  
    -   Directorio del proyecto actual.  \(Puede buscar estos ensamblados utilizando la ficha **Examinar**.\)  
  
    -   Otros directorios del proyecto de la misma solución.  \(Puede buscar estos ensamblados utilizando la ficha **Proyectos**.\)  
  
     o bien  
  
-   Establezca una clave del Registro que especifique la ubicación de los ensamblados que se van a mostrar:  
  
     Para un sistema operativo de 32 bits, agregue una de las siguientes claves del Registro.  
  
    -   \[HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\.NETFramework\\*VersionMinimum*\\AssemblyFoldersEx\\MyAssemblies\]@\="*AssemblyLocation*"  
  
    -   \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\*VersionMinimum*\\AssemblyFoldersEx\\MyAssemblies\]@\="*AssemblyLocation*"  
  
     Para un sistema operativo de 64 bits, agregue una de las siguientes claves del Registro en un subárbol del Registro de 32 bits.  
  
    -   \[HKEY\_CURRENT\_USER\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\*VersionMinimum*\\AssemblyFoldersEx\\MyAssemblies\]@\="*AssemblyLocation*"  
  
    -   \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\*VersionMinimum*\\AssemblyFoldersEx\\MyAssemblies\]@\="*AssemblyLocation*"  
  
     *VersionMinimum* es la versión de .NET Framework más antigua que se aplica.  Si *VersionMinimum* es v3.0, las carpetas especificadas en AssemblyFoldersEx se aplican a proyectos cuyo destino es .NET Framework 3.0 y versiones posteriores.  
  
     *AssemblyLocation* es el directorio de los ensamblados que desea que aparezcan en el cuadro de diálogo **Agregar referencia**, por ejemplo, C:\\MisEnsamblados\\.  
  
     Crear la clave del Registro en el nodo HKEY\_LOCAL\_MACHINE permite que todos los usuarios vean los ensamblados de la ubicación especificada en el cuadro de diálogo **Agregar referencia**.  Crear la clave del Registro en el nodo HKEY\_CURRENT\_USER únicamente afecta a la configuración del usuario actual.  
  
     Abra el cuadro de diálogo **Agregar referencia** de nuevo.  Los ensamblados deben aparecer en la pestaña **.NET**.  En caso contrario, asegúrese de que los ensamblados se encuentren en el directorio *AssemblyLocation* especificado, reinicie Visual Studio e inténtelo de nuevo.  
  
## Pestaña COM  
 La pestaña COM muestra todos los componentes COM a los que se puede hacer referencia.  Si desea agregar una referencia a una DLL COM registrada que contiene un manifiesto interno, quite primero la DLL del Registro.  Si no lo hace, Visual Studio agregará la referencia del ensamblado como un control ActiveX, en lugar de como una DLL nativa.  
  
 Si un tipo de proyecto no admite COM, la pestaña no aparecerá en el cuadro de diálogo **Administrador de referencias**.  
  
## Pestaña Solución  
 La pestaña Solución muestra todos los proyectos compatibles de la solución actual, en la subpestaña Proyectos.  
  
 Un proyecto puede hacer referencia a otro proyecto con una versión de .NET Framework de destino diferente.  Por ejemplo, podría crear un proyecto cuya versión de destino fuera [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] pero que hiciera referencia a un ensamblado compilado para .NET Framework 2.  Sin embargo, el proyecto de .NET Framework 2 no puede hacer referencia a un proyecto de [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].  Para obtener más información, vea [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Un proyecto que tenga como destino [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] es incompatible con un proyecto que tenga como destino [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], se crea una referencia de archivo en lugar de una referencia de proyecto si un proyecto tiene como destino .NET Framework 4 y otro proyecto tiene como destino una versión anterior.  
  
 Un proyecto cuyo destino sea [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] no puede agregar una referencia de proyecto a un proyecto cuyo destino sea .NET Framework, y viceversa.  
  
## Pestaña Windows  
 La pestaña Windows muestra todos los SDK que son específicos de las plataformas en las que se ejecutan sistemas operativos Windows.  
  
 Puede generar un archivo WinMD en Visual Studio de dos maneras:  
  
-   **Proyectos administrados de aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]**: los proyectos de aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] pueden generar archivos binarios WinMD estableciendo Tipo de salida en Archivo WinMD en las propiedades del proyecto.  El nombre de archivo WinMD debe ser el espacio de nombres que engloba a todos los espacios de nombres que existen en él.  Por ejemplo, si un proyecto consta de los espacios de nombres A.B y A.B.C, los nombres posibles para sus archivos WinMD resultantes son A.winmd y A.B.winmd.  Si un usuario especifica un valor del espacio de nombres \(en Propiedades del proyecto, Propiedades del nombre del ensamblado o proyecto\) que diverge del conjunto de espacios de nombres del proyecto, o si no hay un espacio de nombres englobador dentro de un proyecto, se genera una advertencia de compilación: “A.winmd” no es un nombre de archivo .winmd válido para este ensamblado.  Todos los tipos de un archivo de metadatos de Windows deben existir en un subespacio de nombres del nombre de archivo.  Los tipos que no existen en un subespacio de nombres del nombre de archivo no podrán encontrarse en tiempo de ejecución.  En este ensamblado, el espacio de nombres común más pequeño es “CSWSClassLibrary1”.  Un proyecto de escritorio de Visual Basic o Visual C\# solo puede utilizar archivos WinMD que hayan sido generados mediante los SDK de [!INCLUDE[win8](../debugger/includes/win8_md.md)], denominados archivos WinMD propios, y no puede generar archivos WinMD.  
  
-   **Proyectos nativos de aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]**: un archivo WinMD nativo solo contiene metadatos.  Su implementación está en un archivo DLL distinto.  Se pueden generar archivos binarios nativos eligiendo la plantilla del proyecto Componente de Windows en tiempo de ejecución en el cuadro de diálogo **Nuevo proyecto** o empezando un proyecto desde el principio y modificando las propiedades del proyecto para generar un archivo WinMD.  Si el proyecto está compuesto de espacios de nombres dispares, un error de compilación indicará al usuario que combine los espacios de nombres o ejecute la herramienta MSMerge.  
  
 La pestaña Windows se compone de dos subgrupos.  
  
### Subgrupo Principal  
 El subgrupo Principal muestra todos los archivos WinMD \(para los elementos de Windows en tiempo de ejecución\) del SDK de la versión de Windows de destino.  
  
 Los proyectos de aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] contienen referencias a todos los archivos WinMD del SDK de [!INCLUDE[win8](../debugger/includes/win8_md.md)] de forma predeterminada cuando se crea el proyecto.  En los proyectos administrados, un nodo de solo lectura bajo la carpeta Referencias del **Explorador de soluciones** indica la referencia a la versión completa del SDK de [!INCLUDE[win8](../debugger/includes/win8_md.md)].  Por tanto, el subgrupo Principal del Administrador de referencias no mostrará los ensamblados del SDK de [!INCLUDE[win8](../debugger/includes/win8_md.md)], y en su lugar mostrará un mensaje: “Ya se hace referencia a Windows SDK.  Use el Examinador de objetos para explorar las referencias en el Windows SDK".  
  
 En los proyectos de escritorio, el subgrupo Principal no aparece de forma predeterminada.  Puede agregar Windows en tiempo de ejecución abriendo el menú contextual del nodo del proyecto, eligiendo **Descargar el proyecto**, agregando el siguiente fragmento de código y volviendo a abrir el proyecto \(en el nodo del proyecto, elija **Volver a cargar el proyecto**\).  Cuando se invoca el cuadro de diálogo **Administrador de referencias**, aparece el subgrupo Principal.  
  
```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  
  
 Asegúrese de activar la casilla **Windows** en este subgrupo.  Debe poder utilizar elementos de Windows en tiempo de ejecución.  Sin embargo, también conviene agregar System.Runtime, en el que Windows en tiempo de ejecución define algunas clases e interfaces estándar, como IEnumerable, que se utilizan en las bibliotecas de Windows en tiempo de ejecución.  Para obtener información sobre cómo agregar System.Runtime, vea [Aplicaciones de escritorio administradas y Windows en tiempo de ejecución](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).  
  
### Subgrupo Extensiones  
 El subgrupo Extensiones muestra los SDK del usuario que amplían la plataforma Windows de destino.  Esta pestaña aparece únicamente para los proyectos de aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].  Los proyectos de escritorio no mostrarán esta pestaña porque solo pueden usar archivos .winmd propios.  
  
 Un SDK es una colección de archivos que Visual Studio trata como un único componente.  En la pestaña Extensiones, los SDK que se aplican al proyecto desde el que se invocó el cuadro de diálogo **Administrador de referencias** se muestran como entradas individuales.  Cuando se agrega a un proyecto, todo el contenido de los SDK lo utiliza Visual Studio, de modo que el usuario no necesita realizar ninguna acción adicional para usar el contenido de los SDK en IntelliSense, cuadro de herramientas, diseñadores, Explorador de objetos, compilación, implementación, depuración y empaquetado.  Para obtener información sobre cómo mostrar su SDK en la pestaña Extensiones, vea el tema sobre [Crear un Kit de desarrollo de Software](../extensibility/creating-a-software-development-kit.md).  
  
> [!NOTE]
>  Si un proyecto hace referencia a un SDK que depende de otro SDK, Visual Studio no utilizará el segundo SDK a menos que el usuario agregue manualmente una referencia al segundo SDK.  Cuando un usuario elige un SDK en la pestaña **Extensiones**, el cuadro de diálogo **Administrador de referencias** ayuda a identificar las dependencias del SDK al mostrar no solo el nombre y la versión del SDK sino también el nombre de todas las dependencias del SDK en el panel de detalles.  Si un usuario se olvida de las dependencias y solo agrega ese SDK, MSBuild pedirá al usuario que agregue las dependencias.  
  
 Si un tipo de proyecto no admite **Extensiones**, la pestaña no aparecerá en el cuadro de diálogo **Administrador de referencias**.  
  
## Botón Examinar  
 Puede usar el botón **Examinar** para buscar un componente en el sistema de archivos.  
  
 Un proyecto puede hacer referencia a un componente con una versión de .NET Framework de destino diferente.  Por ejemplo, podría crear una aplicación que tuviera como destino .NET Framework 4 Client Profile 4, que hiciera referencia a un componente que tuviera como destino .NET Framework 2.  Para obtener más información, vea [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 No se deben agregar referencias de archivos a resultados de otro proyecto de la misma solución, ya que se pueden producir errores de compilación.  En lugar de ello, use la pestaña **Solución** del cuadro de diálogo **Administrador de referencias** para crear referencias entre proyectos.  Esta táctica facilita el trabajo de desarrollo en equipo, permitiendo una mejor administración de las bibliotecas de clases creadas en los proyectos.  Para obtener más información, vea [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md).  
  
 No puede buscar un SDK y agregarlo al proyecto.  Solo puede buscar un archivo \(por ejemplo, un ensamblado o .winmd\) y agregarlo al proyecto.  
  
 Cuando se hace una referencia a un archivo WinMD, el diseño esperado es que todos los archivos *FileName*.winmd, *FileName*.dll, y *FileName*.pri aparezcan colocados unos junto a otros.  Si hace referencia a un archivo WinMD en los escenarios siguientes, se copiará un conjunto de archivos incompleto en el directorio de resultados del proyecto y, por tanto, se producirán errores de compilación y en tiempo de ejecución.  
  
-   **Componente nativo**: un proyecto nativo creará un archivo WinMD para cada conjunto disjunto de espacios de nombres y un archivo DLL con la implementación.  Los archivos WinMD tendrán nombres dispares.  Al hacer referencia a este archivo de componente nativo, MSBuild no reconocerá que el archivo WinMD con un nombre dispar crea un componente.  Por tanto, solo se copiarán los archivos *FileName*.dll y *FileName*.winmd con idéntico nombre y se producirán errores en tiempo de ejecución.  Para solucionar este problema, cree una SDK de extensión.  Para obtener más información, vea el tema sobre [Crear un Kit de desarrollo de Software](../extensibility/creating-a-software-development-kit.md).  
  
-   **Uso de controles**: como mínimo, un control XAML está compuesto por un *FileName*.winmd, un *FileName*.dll, un *FileName*.pri, un *XamlName*.xaml y un *ImageName*.jpg.  Cuando se compila el proyecto, los archivos de recursos asociados a la referencia de archivo no se copian en el directorio de salida del proyecto, y solo se copian *FileName*.winmd, *FileName*.dll y *FileName*.pri  Se registra un error de compilación para informar al usuario de que faltan los recursos *XamlName*.xaml y *ImageName*.jpg.  Para permitir un funcionamiento correcto, el usuario tendrá que copiar manualmente estos archivos de recursos en el directorio de salida del proyecto para la compilación y depuración\/tiempo de ejecución.  Para solucionar este problema, cree un SDK de extensión siguiendo los pasos que se indican en el tema sobre [Crear un Kit de desarrollo de Software](../extensibility/creating-a-software-development-kit.md) o edite el archivo de proyecto para agregar la siguiente propiedad:  
  
    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  
  
    > [!NOTE]
    >  Si agrega la propiedad, es posible que la compilación se ejecute más lentamente.  
  
## Reciente  
 Los grupos Ensamblados, COM, Windows y Examinar tienen cada uno una pestaña Recientes, que muestra una lista de los componentes que se agregaron recientemente a proyectos.  
  
## Buscar  
 La barra de la búsqueda del cuadro de diálogo **Administrador de referencias** funciona de acuerdo con la pestaña que tiene el foco.  Por ejemplo, si el usuario escribe “System” en la barra de la búsqueda cuando la pestaña **Solución** tiene el foco, la búsqueda no devuelve ningún resultado a menos que la solución conste de un nombre de proyecto que contiene “system”.  
  
## Vea también  
 [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)
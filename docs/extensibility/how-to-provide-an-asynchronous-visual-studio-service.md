---
title: "C&#243;mo: proporcionar un servicio asincr&#243;nico de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: proporcionar un servicio asincr&#243;nico de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si desea obtener un servicio sin bloquear el subproceso de interfaz de usuario, debe crear un servicio asincrónico y cargar el paquete en un subproceso en segundo plano. Para ello puede utilizar un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> en lugar de un <xref:Microsoft.VisualStudio.Shell.Package>, y agregue el servicio con los métodos asincrónicos especial del paquete asincrónica  
  
 Para obtener información acerca de cómo proporcionar servicios de Visual Studio sincrónico, consulte [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md).  
  
## Implementar un servicio asincrónico  
  
1.  Cree un proyecto VSIX \(**archivo \/ nuevo \/ proyecto \/ Visual C\# \/ Extensiblity \/ proyecto VSIX**\). Denomine el proyecto **TestAsync**.  
  
2.  Agregar un paquete VSPackage al proyecto. Seleccione el nodo de proyecto en el **el Explorador de soluciones** y haga clic en **Agregar \/ nuevo elemento o elementos de Visual C\# \/ extensibilidad \/ paquete de Visual Studio**. El nombre de este archivo **TestAsyncPackage.cs**.  
  
3.  En TestAsyncPackage.cs, cambie el paquete para que herede de AsyncPackage en lugar de paquete:  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Para implementar un servicio, debe crear tres tipos:  
  
    -   Interfaz que describe el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método.  
  
    -   Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para implementarse.  
  
    -   Una clase que implementa el servicio y la interfaz de servicio.  
  
5.  En el ejemplo siguiente se muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios. En este ejemplo sólo vamos a agregar el servicio en el archivo de código del paquete.  
  
6.  Agregue las siguientes instrucciones using al archivo de paquete:  
  
    ```c#  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Aquí es la implementación del servicio asincrónico. Tenga en cuenta que debe establecer el proveedor de servicios asincrónica en lugar de con el proveedor de servicio sincrónicas en el constructor:  
  
    ```  
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## Registrar un servicio  
 Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al paquete que proporciona el servicio. Hay dos diferencias de registrar un servicio sincrónico:  
  
-   Si es la carga automática el paquete, debe agregar el <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valor BackgroundLoad al atributo. Para obtener más información sobre VSPackages carga automática, consulte [Cargar VSPackages](../extensibility/loading-vspackages.md).  
  
-   Debe agregar el **AllowsBackgroundLoading \= true** campo el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Para obtener más información acerca de la PackageRegistrationAttribute, consulte [Registrar y anular el registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Este es un ejemplo de un AsyncPackage con un registro de servicio asincrónico::  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## Agregar un servicio  
  
1.  En TestAsyncPackage.cs, quite el `Initialize()` método e invalidar el `InitializeAsync()` método. Agregar el servicio y agregar un método de devolución de llamada para crear los servicios. Este es un ejemplo asincrónico del inicializador de la adición de un servicio:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implemente el método de devolución de llamada como un método asincrónico que crea y devuelve el servicio.  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## Uso de un servicio  
 Ahora puede obtener el servicio y utilizar sus métodos.  
  
1.  Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea utilizar el servicio.  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     No olvide cambiar *\< userpath \>* a un nombre de archivo y ruta de acceso que tenga sentido en su equipo.  
  
2.  Compile y ejecute el código. Cuando aparezca la instancia experimental de Visual Studio, abra una solución. Esto hace que el AsyncPackage para cargar automáticamente. Cuando se ha ejecutado el inicializador, debe buscar un archivo en la ubicación especificada.  
  
## Uso de un servicio asincrónico en un controlador de comandos  
 Este es un ejemplo de cómo utilizar un servicio asincrónico en un comando de menú. Puede utilizar el procedimiento mostrado aquí para utilizar el servicio de otros métodos no son asincrónicos.  
  
1.  Agregar un comando de menú a su proyecto. \(En el **el Explorador de soluciones**, seleccione el nodo del proyecto, con el botón secundario y seleccione **Agregar \/ nuevo elemento \/ extensibilidad comando personalizado**.\) Nombre de archivo de comandos **TestAsyncCommand.cs.**  
  
2.  La plantilla de comando personalizado vuelve a agrega el `Initialize()` método en el archivo TestAsyncPackage.cs para inicializar el comando. En el método Initialize\(\), copie la línea que inicializa el comando. Debería ser similar al siguiente:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Mueva esta línea a la `InitializeAsync()` método en el archivo AsyncPackageForService.cs. Puesto que esto es en la inicialización asincrónica, debe cambiar al subproceso principal antes de inicializar el comando mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ahora debería ser similar al siguiente:  
  
    ```c#  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  Eliminar el `Initialize()` método.  
  
4.  En el archivo TestAsyncCommand.cs, busque la `MenuItemCallback()` método. Elimine el cuerpo del método.  
  
5.  Agregar un uso de la instrucción:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Agregar un método asincrónico denominado `GetAsyncService()`, que obtiene el servicio y utiliza sus métodos:  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Llamar a este método desde el `MenuItemCallback()` método:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Compile la solución e iniciar la depuración. Cuando aparezca la instancia experimental de Visual Studio, vaya a la **herramientas** menú y buscar el **TestAsyncCommand invocar** elemento de menú. Al hacer clic en él, el TextWriterService se escribe en el archivo especificado. \(No necesita abrir una solución, porque al invocar el comando hace que el paquete que desea cargar.\)  
  
## Vea también  
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)
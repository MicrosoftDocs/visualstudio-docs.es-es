---
title: 'Cómo: proporcionar un servicio de asincrónica de Visual Studio | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4754ccf4a7a66151ad8fb351996c1520dc9483c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Cómo: proporcionar un servicio de asincrónica de Visual Studio
Si desea obtener un servicio sin bloquear el subproceso de interfaz de usuario, debe crear un servicio asincrónico y cargar el paquete en un subproceso en segundo plano. Para ello puede usar un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> en lugar de un <xref:Microsoft.VisualStudio.Shell.Package>y agregue el servicio con los métodos asincrónicos especial del paquete asincrónica.
  
 Para obtener información acerca de cómo proporcionar servicios de Visual Studio sincrónicos, vea [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implementar un servicio asincrónico  
  
1.  Cree un proyecto VSIX (**archivo > Nuevo > proyecto > Visual C# > Extensiblity > proyecto VSIX**). Denomine el proyecto **TestAsync**.  
  
2.  Agregar un paquete VSPackage al proyecto. Seleccione el nodo de proyecto en el **el Explorador de soluciones** y haga clic en **Agregar > nuevo elemento > elementos de Visual C# > extensibilidad > paquete de Visual Studio**. Llamar a este archivo **TestAsyncPackage.cs**.  
  
3.  En TestAsyncPackage.cs, cambie el paquete para que herede de AsyncPackage en lugar de paquete:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Para implementar un servicio, debe crear tres tipos:  
  
    -   Una interfaz que identifica el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método solo cuando se utilicen para consultar el servicio.
  
    -   Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para que se implementen.  
  
    -   Una clase que implementa el servicio y la interfaz de servicio.  
  
5.  En el ejemplo siguiente se muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios. En este ejemplo solo se agregará el servicio en el archivo de código del paquete.  
  
6.  Agregue las siguientes instrucciones using al archivo de paquete:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Esta es la implementación del servicio asincrónico. Tenga en cuenta que debe establecer el proveedor de servicios asincrónica en lugar de con el proveedor de servicio sincrónicas en el constructor:  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private IAsyncServiceProvider asyncServiceProvider;  
        
        public TextWriterService(IAsyncServiceProvider provider)  
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;  
        }
        
        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            // We have to use JoinableTaskFactory as code will switch to main thread in some parts
            await ThreadHelper.JoinableTaskFactory.RunAsync(async () =>
            {
                await TaskScheduler.Default;
                // do background operations that involve IO or other async methods
                
                await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
                // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
                // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.
                
                IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
                // use Visual Studio services to continue initialization
            });
        }
        
        public async Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
    }  

    public interface STextWriterService  
    {  
    }  
    
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
    }  
    ```  
  
## <a name="registering-a-service"></a>Registrar un servicio  
 Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al paquete que proporciona el servicio. Diferentes para registrar un servicio sincrónico, tiene que asegurarse de paquete y el servicio admite async cargar:
  
-   Debe agregar el **AllowsBackgroundLoading = true** campo a la <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> para garantizar el paquete se puede inicializar de forma asincrónica para obtener más información sobre la PackageRegistrationAttribute, consulte [registrar y Al anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
-   Debe agregar el **IsAsyncQueryable = true** campo el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> para garantizar la instancia de servicio se puede inicializar de forma asincrónica.

 Este es un ejemplo de un AsyncPackage con un registro de servicio asincrónica:
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Agregar un servicio  
  
1.  En TestAsyncPackage.cs, quite el `Initialize()` método e invalide el `InitializeAsync()` método. Agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es un ejemplo del inicializador asincrónico agregar un servicio:  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implemente el método de devolución de llamada como un método asincrónico que crea y devuelve el servicio.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="using-a-service"></a>Uso de un servicio  
 Ahora puede hacer que el servicio y utilizar sus métodos.  
  
1.  Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea usar el servicio.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
  
    }  
  
    ```  
  
     No olvide cambiar  *\<userpath >* a un nombre de archivo y ruta de acceso que tenga sentido en su equipo.  
  
2.  Compile y ejecute el código. Cuando aparezca la instancia experimental de Visual Studio, abra una solución. Esto hace que la AsyncPackage a cargar automáticamente. Cuando se haya ejecutado el inicializador, debe buscar un archivo en la ubicación especificada.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Uso de un servicio asincrónico en un controlador de comandos.  
 Este es un ejemplo de cómo utilizar un servicio asincrónico en un comando de menú. Puede usar el procedimiento que se muestra aquí para utilizar el servicio de otros métodos no son asincrónicos.  
  
1.  Agregue un comando de menú a su proyecto. (En el **el Explorador de soluciones**, seleccione el nodo del proyecto, menú contextual y seleccione **Agregar / nuevo elemento / extensibilidad / comando personalizado**.) Nombre del archivo de comandos **TestAsyncCommand.cs.**  
  
2.  La plantilla del comando personalizado vuelve a agrega el `Initialize()` método en el archivo TestAsyncPackage.cs para inicializar el comando. En el método Initialize(), copie la línea que inicializa el comando. El resultado debería tener un aspecto similar a este:  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Mover esta línea para que la `InitializeAsync()` método en el archivo AsyncPackageForService.cs. Puesto que se trata de una inicialización asincrónica, debe cambiar al subproceso principal antes de inicializar el comando mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ahora debería ser similar al siguiente:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  Eliminar el `Initialize()` método.  
  
4.  En el archivo TestAsyncCommand.cs, busque la `MenuItemCallback()` método. Elimine el cuerpo del método.  
  
5.  Agregue una instrucción using:  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Agregar un método asincrónico denominado `UseTextWriterAsync()`, que obtiene el servicio y utiliza sus métodos:  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Llamar a este método desde el `MenuItemCallback()` método:  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Compile la solución y comience la depuración. Cuando aparezca la instancia experimental de Visual Studio, vaya a la **herramientas** menú y busque la **TestAsyncCommand invocar** elemento de menú. Al hacer clic en él, el TextWriterService se escribe en el archivo especificado. (No necesita abrir una solución, dado que al invocar el comando también hace que el paquete que desea cargar.)  
  
## <a name="see-also"></a>Vea también  
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)

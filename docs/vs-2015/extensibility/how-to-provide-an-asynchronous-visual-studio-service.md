---
title: 'Cómo: proporcionar un servicio asincrónico de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1938a3a8b5b0eb3c0cc7b062d6d43c4e869397eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851982"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Cómo: proporcionar un servicio asincrónico de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si desea obtener un servicio sin bloquear el subproceso de interfaz de usuario, debe crear un servicio asincrónico y cargar el paquete en un subproceso en segundo plano. Para ello puede usar un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> en lugar de un <xref:Microsoft.VisualStudio.Shell.Package>y agregue el servicio con los métodos asincrónicos especial del paquete asincrónica  
  
 Para obtener información acerca de cómo proporcionar servicios de Visual Studio sincrónicos, vea [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implementar un servicio asincrónico  
  
1.  Cree un proyecto VSIX (**archivo / nuevo / proyecto / Visual C# / usaría / proyecto VSIX**). Denomine el proyecto **TestAsync**.  
  
2.  Agregar un paquete VSPackage al proyecto. Seleccione el nodo del proyecto en el **el Explorador de soluciones** y haga clic en **Agregar / nuevo elemento o elementos de Visual C# / extensibilidad / paquete de Visual Studio**. Nombre de este archivo **TestAsyncPackage.cs**.  
  
3.  En TestAsyncPackage.cs, cambie el paquete para heredar de AsyncPackage en lugar de paquete:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Para implementar un servicio, deberá crear tres tipos:  
  
    -   Interfaz que describe el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método.  
  
    -   Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para implementarse.  
  
    -   Una clase que implementa el servicio y la interfaz de servicio.  
  
5.  El ejemplo siguiente muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios. En este ejemplo simplemente vamos a agregar el servicio al archivo de código del paquete.  
  
6.  Agregue las siguientes instrucciones using al archivo de paquete:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Esta es la implementación de servicio asincrónicas. Tenga en cuenta que deberá establecer el proveedor de servicios asincrónica en lugar de con el proveedor de servicio sincrónicas en el constructor:  
  
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
  
## <a name="registering-a-service"></a>Registrar un servicio  
 Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al paquete que proporciona el servicio. Hay dos diferencias al registrar un servicio sincrónico:  
  
- Si es la carga automática del paquete, debe agregar el <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valor BackgroundLoad al atributo. Para obtener más información sobre los VSPackages carga automática, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
- Debe agregar el **AllowsBackgroundLoading = true** campo el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Para obtener más información sobre la PackageRegistrationAttribute, consulte [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
  Este es un ejemplo de un AsyncPackage con un registro de servicio asincrónico::  
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Agregar un servicio  
  
1.  En TestAsyncPackage.cs, quite el `Initialize()` método e invalide el `InitializeAsync()` método. Agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es un ejemplo asincrónico del inicializador de la adición de un servicio:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implemente el método de devolución de llamada como un método asincrónico que crea y devuelve el servicio.  
  
    ```csharp  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## <a name="using-a-service"></a>Uso de un servicio  
 Ahora puede obtener el servicio y usar sus métodos.  
  
1.  Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea usar el servicio.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     No olvide cambiar  *\<userpath >* a un nombre de archivo y ruta de acceso que tenga sentido en su equipo.  
  
2.  Compile y ejecute el código. Cuando aparezca la instancia experimental de Visual Studio, abra una solución. Esto hace que el AsyncPackage para cargar automáticamente. Cuando se haya ejecutado el inicializador, encontrará un archivo en la ubicación especificada.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Uso de un servicio asincrónico en un controlador de comandos  
 Este es un ejemplo de cómo usar un servicio asincrónico en un comando de menú. Puede usar el procedimiento mostrado aquí para usar el servicio de otros métodos que no son asincrónicos.  
  
1.  Agregar un comando de menú al proyecto. (En el **el Explorador de soluciones**, seleccione el nodo del proyecto, secundario y seleccione **Agregar / nuevo elemento / extensibilidad / comandos personalizados**.) Nombre del archivo de comandos **TestAsyncCommand.cs.**  
  
2.  La plantilla comando personalizado vuelve a agrega el `Initialize()` método al archivo TestAsyncPackage.cs con el fin de inicializar el comando. En el método Initialize(), copie la línea que inicializa el comando. El resultado debería tener un aspecto similar a este:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Mover esta línea a la `InitializeAsync()` método en el archivo AsyncPackageForService.cs. Puesto que se trata de una inicialización asincrónica, debe cambiar al subproceso principal antes de inicializar el comando mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ahora debe ser similar al siguiente:  
  
    ```csharp  
  
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
  
4.  En el archivo TestAsyncCommand.cs, busque el `MenuItemCallback()` método. Elimine el cuerpo del método.  
  
5.  Agregue una instrucción using:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Agregar un método asincrónico denominado `GetAsyncService()`, que obtiene el servicio y usa sus métodos:  
  
    ```csharp  
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
  
8.  Compile la solución y comience la depuración. Cuando aparezca la instancia experimental de Visual Studio, vaya a la **herramientas** menú y buscar el **TestAsyncCommand invocar** elemento de menú. Al hacer clic en él, el TextWriterService escribe en el archivo especificado. (No deberá abrir una solución, ya que también al invocar el comando hace que el paquete cargar.)  
  
## <a name="see-also"></a>Vea también  
 [Uso y provisión de servicios](../extensibility/using-and-providing-services.md)


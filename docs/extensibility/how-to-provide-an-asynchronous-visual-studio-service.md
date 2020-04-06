---
title: 'Cómo: Proporcionar un servicio de Visual Studio asincrónico ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710766"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Cómo: Proporcionar un servicio asincrónico de Visual Studio
Si desea obtener un servicio sin bloquear el subproceso de interfaz de usuario, debe crear un servicio asincrónico y cargar el paquete en un subproceso en segundo plano. Para este propósito, <xref:Microsoft.VisualStudio.Shell.AsyncPackage> puede usar <xref:Microsoft.VisualStudio.Shell.Package>un valor , en lugar de un , y agregar el servicio con los métodos asincrónicos especiales del paquete asincrónico.

 Para obtener información acerca de cómo proporcionar servicios de Visual Studio sincrónicos, vea [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementar un servicio asincrónico

1. Crear un proyecto VSIX (**Archivo** > **Nuevo** > **proyecto** > Proyecto de Visual**C-** > **Extensiblity** > **VSIX Project**). Asigne al proyecto el nombre **TestAsync**.

2. Agregue un VSPackage al proyecto. Seleccione el nodo del proyecto en el **Explorador** de soluciones y haga clic en **Agregar** > **nuevo elemento** > Paquete de**extensibilidad** > de**elementos** > de**Visual Studio**. Asigne a este archivo el *nombre TestAsyncPackage.cs*.

3. En *TestAsyncPackage.cs*, cambie el `AsyncPackage` paquete `Package`para heredar de en lugar de:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Para implementar un servicio, debe crear tres tipos:

    - Interfaz que identifica el servicio. Muchas de estas interfaces están vacías, es decir, no tienen métodos, ya que solo se utilizan para consultar el servicio.

    - Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos que se van a implementar.

    - Una clase que implementa el servicio y la interfaz de servicio.

5. En el ejemplo siguiente se muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios. En este ejemplo, solo agregaremos el servicio al archivo de código del paquete.

6. Agregue las siguientes directivas using al archivo de paquete:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Aquí está la implementación del servicio asincrónico. Tenga en cuenta que debe establecer el proveedor de servicios asincrónicos en lugar del proveedor de servicios sincrónico en el constructor:

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
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
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

## <a name="register-a-service"></a>Registrar un servicio
 Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> paquete que proporciona el servicio. A diferencia del registro de un servicio sincrónico, debe asegurarse de que tanto el paquete como el servicio admiten la carga asincrónica:

- Debe agregar el campo **AllowsBackgroundLoading** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> - true al para asegurarse de que el paquete se puede inicializar de forma asincrónica Para obtener más información acerca de PackageRegistrationAttribute, vea [Registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Debe agregar el campo **IsAsyncQueryable** <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> - true al para asegurarse de que la instancia de servicio se puede inicializar de forma asincrónica.

  A continuación se `AsyncPackage` muestra un ejemplo de un registro de servicio asincrónico:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Agregar un servicio

1. En *TestAsyncPackage.cs*, `Initialize()` quite el `InitializeAsync()` método e invalide el método. Agregue el servicio y agregue un método de devolución de llamada para crear los servicios. A continuación se muestra un ejemplo del inicializador asincrónico que agrega un servicio:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Para que este servicio sea visible fuera de este paquete, establezca el valor de marca de promoción en *true* como último parámetro:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Agregue una referencia a *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implemente el método de devolución de llamada como un método asincrónico que crea y devuelve el servicio.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Usar un servicio
 Ahora puede obtener el servicio y utilizar sus métodos.

1. Lo mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desee usar el servicio.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     No se olvide `userpath` de cambiar a un nombre de archivo y ruta que tiene sentido en su máquina!

2. Compile y ejecute el código. Cuando aparezca la instancia experimental de Visual Studio, abra una solución. Esto hace `AsyncPackage` que la carga automática. Cuando se haya ejecutado el inicializador, debe buscar un archivo en la ubicación especificada.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Usar un servicio asincrónico en un controlador de comandos
 Este es un ejemplo de cómo utilizar un servicio asincrónico en un comando de menú. Puede usar el procedimiento que se muestra aquí para utilizar el servicio en otros métodos no asincrónicos.

1. Agregue un comando de menú al proyecto. (En el **Explorador**de soluciones , seleccione el nodo del proyecto, haga clic con el botón derecho y seleccione **Agregar** > nuevo comando**personalizado**de**extensibilidad** > de**elementos** > .) Asigne al archivo de comandos el *nombre TestAsyncCommand.cs*.

2. La plantilla de comando personalizada `Initialize()` vuelve a agregar el método al archivo *TestAsyncPackage.cs* para inicializar el comando. En `Initialize()` el método, copie la línea que inicializa el comando. Debería ser parecido a este:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Mueva esta línea `InitializeAsync()` al método del archivo *AsyncPackageForService.cs.* Puesto que esto se encuentra en una inicialización asincrónica, debe <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>cambiar al subproceso principal antes de inicializar el comando mediante . Debería ser parecido a este:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Elimine `Initialize()` el método.

4. En el *archivo TestAsyncCommand.cs,* busque el `MenuItemCallback()` método. Elimine el cuerpo del método.

5. Agregue una directiva using:

    ```csharp
    using System.IO;
    ```

6. Agregue un método `UseTextWriterAsync()`asincrónico denominado , que obtiene el servicio y utiliza sus métodos:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Llame a este `MenuItemCallback()` método desde el método:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compile la solución y comience la depuración. Cuando aparezca la instancia experimental de Visual Studio, vaya al menú **Herramientas** y busque el elemento de menú **Invocar TestAsyncCommand.** Al hacer clic en él, TextWriterService escribe en el archivo especificado. (No es necesario abrir una solución, porque invocar el comando también hace que el paquete se cargue.)

## <a name="see-also"></a>Vea también
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)

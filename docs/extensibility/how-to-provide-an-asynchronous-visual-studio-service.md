---
title: Procedimiento Proporciona un servicio asincrónico de Visual Studio | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9a03c4282fb7c2719f0f408759be972ead0f866
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110302"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Procedimiento Proporcionar un servicio asincrónico de Visual Studio
Si desea obtener un servicio sin bloquear el subproceso de interfaz de usuario, debe crear un servicio asincrónico y cargar el paquete en un subproceso en segundo plano. Para ello puede usar un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> en lugar de un <xref:Microsoft.VisualStudio.Shell.Package>y agregue el servicio con los métodos asincrónicos especial del paquete asincrónica.

 Para obtener información acerca de cómo proporcionar servicios de Visual Studio sincrónicos, vea [Cómo: Proporcionar un servicio](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementar un servicio asincrónico

1. Cree un proyecto VSIX (**archivo** > **New** > **proyecto** > **Visual C#**  >  **Usaría** > **proyecto VSIX**). Denomine el proyecto **TestAsync**.

2. Agregar un paquete VSPackage al proyecto. Seleccione el nodo del proyecto en el **el Explorador de soluciones** y haga clic en **agregar** > **nuevo elemento** > **Visual C# elementos**  >  **Extensibilidad** > **paquete de Visual Studio**. Nombre de este archivo *TestAsyncPackage.cs*.

3. En *TestAsyncPackage.cs*, cambiar el paquete que se va a heredar `AsyncPackage` lugar `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Para implementar un servicio, deberá crear tres tipos:

    - Una interfaz que identifica el servicio. Muchas de estas interfaces están vacíos, es decir, no tienen ningún método como solo se usan para consultar el servicio.

    - Interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos para implementarse.

    - Una clase que implementa el servicio y la interfaz de servicio.

5. El ejemplo siguiente muestra una implementación muy básica de los tres tipos. El constructor de la clase de servicio debe establecer el proveedor de servicios. En este ejemplo simplemente vamos a agregar el servicio al archivo de código del paquete.

6. Agregue las siguientes instrucciones using al archivo de paquete:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Esta es la implementación de servicio asincrónicas. Tenga en cuenta que deberá establecer el proveedor de servicios asincrónica en lugar de con el proveedor de servicio sincrónicas en el constructor:

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

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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
 Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al paquete que proporciona el servicio. Diferentes para registrar un servicio sincrónico, tiene que asegurarse de paquete y servicio admite async carga:

- Debe agregar el **AllowsBackgroundLoading = true** campo el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> para garantizar el paquete se puede inicializar de forma asincrónica para obtener más información sobre la PackageRegistrationAttribute, consulte [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Debe agregar el **IsAsyncQueryable = true** campo el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> para garantizar la instancia de servicio se puede inicializar de forma asincrónica.

  Este es un ejemplo de un `AsyncPackage` con un registro de servicio asincrónico:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Agregar un servicio

1. En *TestAsyncPackage.cs*, quite el `Initialize()` método e invalide el `InitializeAsync()` método. Agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es un ejemplo asincrónico del inicializador de la adición de un servicio:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

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
 Ahora puede obtener el servicio y usar sus métodos.

1. Le mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar que desea usar el servicio.

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

2. Compile y ejecute el código. Cuando aparezca la instancia experimental de Visual Studio, abra una solución. Esto hace que el `AsyncPackage` para cargar automáticamente. Cuando se haya ejecutado el inicializador, encontrará un archivo en la ubicación especificada.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Usar un servicio asincrónico en un controlador de comandos
 Este es un ejemplo de cómo usar un servicio asincrónico en un comando de menú. Puede usar el procedimiento mostrado aquí para usar el servicio de otros métodos que no son asincrónicos.

1. Agregar un comando de menú al proyecto. (En el **el Explorador de soluciones**, seleccione el nodo del proyecto, secundario y seleccione **agregar** > **nuevo elemento**  >   **Extensibilidad** > **comando personalizado**.) Nombre del archivo de comandos *TestAsyncCommand.cs*.

2. La plantilla comando personalizado vuelve a agrega el `Initialize()` método para el *TestAsyncPackage.cs* archivo con el fin de inicializar el comando. En el `Initialize()` método, copie la línea que inicializa el comando. El resultado debería tener un aspecto similar a este:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Mover esta línea a la `InitializeAsync()` método en el *AsyncPackageForService.cs* archivo. Puesto que se trata de una inicialización asincrónica, debe cambiar al subproceso principal antes de inicializar el comando mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ahora debe ser similar al siguiente:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync((<userpath>, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Eliminar el `Initialize()` método.

4. En el *TestAsyncCommand.cs* de archivos, busque el `MenuItemCallback()` método. Elimine el cuerpo del método.

5. Agregue una instrucción using:

    ```csharp
    using System.IO;
    ```

6. Agregar un método asincrónico denominado `UseTextWriterAsync()`, que obtiene el servicio y usa sus métodos:

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

7. Llamar a este método desde el `MenuItemCallback()` método:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compile la solución y comience la depuración. Cuando aparezca la instancia experimental de Visual Studio, vaya a la **herramientas** menú y buscar el **TestAsyncCommand invocar** elemento de menú. Al hacer clic en él, el TextWriterService escribe en el archivo especificado. (No deberá abrir una solución, ya que también al invocar el comando hace que el paquete cargar.)

## <a name="see-also"></a>Vea también
- [Usar y proporcionan servicios](../extensibility/using-and-providing-services.md)

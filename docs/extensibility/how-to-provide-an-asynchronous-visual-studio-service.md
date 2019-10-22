---
title: 'Cómo: proporcionar un servicio de Visual Studio asincrónico | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c34995a49a785061c67f1324c9c9cd5b5316178
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633122"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Cómo: proporcionar un servicio de Visual Studio asincrónico
Si desea obtener un servicio sin bloquear el subproceso de la interfaz de usuario, debe crear un servicio asincrónico y cargar el paquete en un subproceso en segundo plano. Para ello, puede usar un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> en lugar de un <xref:Microsoft.VisualStudio.Shell.Package> y agregar el servicio con los métodos asincrónicos especiales del paquete asincrónico.

 Para obtener información sobre cómo proporcionar servicios sincrónicos de Visual Studio, consulte [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementar un servicio asincrónico

1. Cree un proyecto de VSIX (**archivo**  > **nuevo** **proyecto** de  >   > **Visual C#**   > **usaría** 0**Proyecto VSIX**). Asigne al proyecto el nombre **TestAsync**.

2. Agregue un VSPackage al proyecto. Seleccione el nodo del proyecto en el **Explorador de soluciones** y haga clic en **Agregar**  > **nuevo elemento**  > **elementos visuales C#**   > **extensibilidad**  >  paquete de**Visual Studio**. Asigne a este archivo el nombre *TestAsyncPackage.CS*.

3. En *TestAsyncPackage.CS*, cambie el paquete para que herede de `AsyncPackage` en lugar de `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Para implementar un servicio, debe crear tres tipos:

    - Interfaz que identifica el servicio. Muchas de estas interfaces están vacías, es decir, no tienen métodos, ya que solo se usan para consultar el servicio.

    - Una interfaz que describe la interfaz de servicio. Esta interfaz incluye los métodos que se van a implementar.

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

7. Esta es la implementación de servicio asincrónica. Tenga en cuenta que debe establecer el proveedor de servicios asincrónico en lugar del proveedor de servicios sincrónicos en el constructor:

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
 Para registrar un servicio, agregue el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> al paquete que proporciona el servicio. En lo que se refiere al registro de un servicio sincrónico, tiene que asegurarse de que tanto el paquete como el servicio admiten la carga asincrónica:

- Debe agregar el campo **AllowsBackgroundLoading = true** al <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> para asegurarse de que el paquete se pueda inicializar de forma asincrónica para obtener más información sobre PackageRegistrationAttribute, vea [registrar y](../extensibility/registering-and-unregistering-vspackages.md)anular el registro de VSPackages.

- Debe agregar el campo **IsAsyncQueryable = true** al <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> para asegurarse de que la instancia de servicio se puede inicializar de forma asincrónica.

  A continuación se muestra un ejemplo de un `AsyncPackage` con un registro de servicio asincrónico:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Agregar un servicio

1. En *TestAsyncPackage.CS*, quite el método `Initialize()` e invalide el método `InitializeAsync()`. Agregue el servicio y agregue un método de devolución de llamada para crear los servicios. Este es un ejemplo del inicializador asincrónico que agrega un servicio:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. Agregue una referencia a *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime. dll*.

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

1. Lo mostraremos en el inicializador, pero puede obtener el servicio en cualquier lugar en el que desee usar el servicio.

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

     No olvide cambiar `userpath` por un nombre de archivo y una ruta de acceso que tenga sentido en el equipo.

2. Compile y ejecute el código. Cuando aparezca la instancia experimental de Visual Studio, abra una solución. Esto hace que se cargue el `AsyncPackage`. Cuando se haya ejecutado el inicializador, debe buscar un archivo en la ubicación especificada.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Usar un servicio asincrónico en un controlador de comandos
 A continuación se muestra un ejemplo de cómo usar un servicio asincrónico en un comando de menú. Puede usar el procedimiento que se muestra aquí para usar el servicio en otros métodos no asincrónicos.

1. Agregue un comando de menú al proyecto. (En el **Explorador de soluciones**, seleccione el nodo del proyecto, haga clic con el botón derecho y seleccione **Agregar**  > **nuevo elemento**  > **extensibilidad**  > **comando personalizado**). Asigne al archivo de comandos el nombre *TestAsyncCommand.CS*.

2. La plantilla de comandos personalizada vuelve a agregar el método `Initialize()` al archivo *TestAsyncPackage.CS* para inicializar el comando. En el método `Initialize()`, copie la línea que inicializa el comando. El resultado debería tener un aspecto similar a este:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Mueva esta línea al método `InitializeAsync()` del archivo *AsyncPackageForService.CS* . Dado que se trata de una inicialización asincrónica, debe cambiar al subproceso principal antes de inicializar el comando mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Ahora debería tener el siguiente aspecto:

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

3. Elimine el método `Initialize()`.

4. En el archivo *TestAsyncCommand.CS* , busque el método `MenuItemCallback()`. Elimine el cuerpo del método.

5. Agregue una directiva using:

    ```csharp
    using System.IO;
    ```

6. Agregue un método asincrónico denominado `UseTextWriterAsync()`, que obtiene el servicio y utiliza sus métodos:

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

7. Llame a este método desde el método `MenuItemCallback()`:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Compile la solución y comience la depuración. Cuando aparezca la instancia experimental de Visual Studio, vaya al menú **herramientas** y busque el elemento de menú **invocar TestAsyncCommand** . Al hacer clic en él, el TextWriterService escribe en el archivo especificado. (No es necesario abrir una solución, ya que al invocar el comando también se carga el paquete).

## <a name="see-also"></a>Vea también
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)

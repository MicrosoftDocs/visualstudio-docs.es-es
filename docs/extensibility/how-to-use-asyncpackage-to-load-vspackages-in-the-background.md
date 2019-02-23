---
title: Filtrar Uso de AsyncPackage para cargar VSPackages en segundo plano | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8a0de1ccf4a75bb10ae120e9237ceb176a3794a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680989"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Filtrar Uso de AsyncPackage para cargar VSPackages en segundo plano
Cargar e inicializar un paquete de VS pueden dar lugar a E/S de disco. Si se produce este tipo de E/S en el subproceso de interfaz de usuario, puede provocar problemas de capacidad de respuesta. Para solucionar este problema, Visual Studio 2015 introdujo la <xref:Microsoft.VisualStudio.Shell.AsyncPackage> clase que habilita la carga del paquete en un subproceso en segundo plano.

## <a name="create-an-asyncpackage"></a>Crear un AsyncPackage
 Puede empezar creando un proyecto VSIX (**archivo** > **New** > **proyecto** > **Visual C#**   >  **Extensibilidad** > **proyecto VSIX**) y la adición de un VSPackage al proyecto (haga doble clic en el proyecto y **agregar**  >  **Nuevo elemento**  >   **C# elemento** > **extensibilidad**  >   **Paquete de Visual Studio**). A continuación, puede crear sus servicios y agregar esos servicios a su paquete.

1. Derivar el paquete desde <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.

2. Si va a proporcionar servicios cuya consulta puede provocar cargue el paquete:

    Para indicar a Visual Studio que el paquete es seguro para la carga en segundo plano y para participar en este comportamiento, su <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> debe establecer **AllowsBackgroundLoading** propiedad en true en el constructor de atributo.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Para indicar a Visual Studio que es seguro crear una instancia del servicio en un subproceso en segundo plano, debe establecer el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propiedad en true en el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructor.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Si va a cargar a través de los contextos de interfaz de usuario, a continuación, se debe especificar **PackageAutoLoadFlags.BackgroundLoad** para el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o el valor (0 x 2) en las marcas se escribe como el valor de entrada de carga automática de su paquete.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Si tiene trabajo asincrónico de inicialización, se debe reemplazar <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Quitar el `Initialize()` método proporcionado por la plantilla de VSIX. (El `Initialize()` método **AsyncPackage** está sellado). Puede usar cualquiera de los <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> métodos para agregar los servicios asincrónicos al paquete.

    NOTA: Para llamar a `base.InitializeAsync()`, puede cambiar el código fuente para:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Debe tener cuidado para no realizar llamadas RPC (llamada a procedimiento remoto) desde el código de inicialización asincrónica (en **InitializeAsync**). Estos pueden producirse cuando se llama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directa o indirectamente.  Cuando se requieren las cargas de sincronización, el subproceso de interfaz de usuario se bloqueará con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. El modelo bloqueo predeterminada deshabilita RPC. Esto significa que si intenta usar una llamada RPC de sus tareas asincrónicas, generará un interbloqueo si el subproceso de interfaz de usuario es esperando cargue el paquete. La alternativa general es calcular las referencias en el código para el subproceso de interfaz de usuario si es necesario usar algo como **generador de tareas Joinable**del <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o algún otro mecanismo que no usa una RPC.  No use **ThreadHelper.Generic.Invoke** o generalmente bloquea el subproceso que realiza la llamada espera obtener en el subproceso de interfaz de usuario.

    NOTA: Debe evitar usar **GetService** o **QueryService** en su `InitializeAsync` método. Si tiene que usarlos, deberá cambiar al subproceso de interfaz de usuario en primer lugar. La alternativa es usar <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> desde su **AsyncPackage** (convirtiéndola en <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C#: Crear un AsyncPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertir un VSPackage existente para AsyncPackage
 La mayoría del trabajo es lo mismo que crear un nuevo **AsyncPackage**. Siga los pasos 1 a 5 anteriores. También debe tener cautela con las siguientes recomendaciones:

1.  No olvide quitar el `Initialize` invalidación que tenía en el paquete.

2.  Evitar los interbloqueos: Podría haber oculto de RPC en el código. que tienen lugar en un subproceso en segundo plano. Asegúrese de que si está realizando una llamada RPC (por ejemplo, **GetService**), necesita para cambiar al subproceso principal (1) o (2) use la versión asincrónica de la API si existe (por ejemplo, **GetServiceAsync**).

3.  No alterne entre los subprocesos con demasiada frecuencia. Intenta localizar el trabajo que se puede producir en un subproceso en segundo plano para reducir el tiempo de carga.

## <a name="querying-services-from-asyncpackage"></a>Consultar los servicios de AsyncPackage
 Un **AsyncPackage** puede o no puede cargar de forma asincrónica según el autor de llamada. Por ejemplo,

- Si el llamador llamado **GetService** o **QueryService** (ambas API sincrónico) o

- Si el llamador llamado **IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o

- La carga se desencadena mediante un contexto de interfaz de usuario, pero no especificó que el mecanismo de contexto de interfaz de usuario puede cargar asincrónicamente

  a continuación, el paquete se cargará sincrónicamente.

  El paquete todavía tiene una oportunidad (en su fase de inicialización asincrónica) para realizar el trabajo fuera del subproceso de interfaz de usuario, aunque se bloqueará el subproceso de interfaz de usuario para la finalización de ese trabajo. Si el llamador utiliza **IAsyncServiceProvider** a asincrónicamente la consulta para el servicio, a continuación, la carga e inicialización se hará asincrónicamente suponiendo que no se bloquean inmediatamente en el objeto de la tarea resultante.

  C#: Cómo consultar el servicio de forma asincrónica:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```

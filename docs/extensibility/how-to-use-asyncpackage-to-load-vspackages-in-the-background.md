---
title: 'Cómo: Usar AsyncPackage para cargar VSPackages en segundo plano ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710617"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Cómo: Usar AsyncPackage para cargar VSPackages en segundo plano
Cargar e inicializar un paquete VS puede dar lugar a E/S de disco. Si dicha E/S se produce en el subproceso de interfaz de usuario, puede provocar problemas de capacidad de respuesta. Para solucionar este tema, Visual Studio <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 2015 introdujo la clase que permite la carga de paquetes en un subproceso en segundo plano.

## <a name="create-an-asyncpackage"></a>Crear un AsyncPackage
 Puede empezar por crear un proyecto VSIX **(Proyecto** > **New** > **Project** > **VSIX**de extensión de proyecto de archivo de Visual**C)** > **Extensibility** > y agregar un VSPackage al proyecto (haga clic con el botón derecho en el proyecto y **agregar** > **nuevo** > **elemento** > de paquete de**Visual Studio**de la**extensibilidad** > ). A continuación, puede crear los servicios y agregarlos al paquete.

1. Derive el <xref:Microsoft.VisualStudio.Shell.AsyncPackage>paquete de .

2. Si proporciona servicios cuyas consultas pueden hacer que el paquete se cargue:

    Para indicar a Visual Studio que el paquete es seguro para <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> la carga en segundo plano y para optar por este comportamiento, debe establecer **AllowsBackgroundLoading** propiedad true en el constructor de atributos.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Para indicar a Visual Studio que es seguro crear instancias del <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> servicio en <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> un subproceso en segundo plano, debe establecer la propiedad en true en el constructor.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Si va a cargar a través de contextos de interfaz <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> de usuario, debe especificar **PackageAutoLoadFlags.BackgroundLoad** para el valor OR (0x2) en las marcas escritas como el valor de la entrada de carga automática del paquete.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Si tiene que realizar un trabajo <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>de inicialización asincrónica, debe invalidar . Quite `Initialize()` el método proporcionado por la plantilla VSIX. (El `Initialize()` método de **AsyncPackage** está sellado). Puede usar cualquiera <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> de los métodos para agregar servicios asincrónicos al paquete.

    NOTA: Para `base.InitializeAsync()`llamar a , puede cambiar el código fuente a:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Debe tener cuidado de NO realizar RPC (llamada a procedimiento remoto) a partir del código de inicialización asincrónico (en **InitializeAsync**). Estos pueden ocurrir <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> cuando se llama directa o indirectamente.  Cuando se requieren cargas de sincronización, el subproceso de interfaz de usuario bloqueará mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. El modelo de bloqueo predeterminado deshabilita las RPC. Esto significa que si intenta usar un RPC de sus tareas asincrónicas, interbloqueo si el subproceso de interfaz de usuario está esperando a que se cargue el paquete. La alternativa general es calcular las referencias del código al subproceso de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> interfaz de usuario si es necesario mediante algo como **Unable Task Factory**'s o algún otro mecanismo que no use un RPC.  NO use **ThreadHelper.Generic.Invoke** o, por lo general, bloquee el subproceso que realiza la llamada en espera para llegar al subproceso de interfaz de usuario.

    NOTA: Debe evitar el uso de `InitializeAsync` **GetService** o **QueryService** en el método. Si tiene que usarlos, primero tendrá que cambiar al subproceso de interfaz de usuario. La alternativa es <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> usar desde el **AsyncPackage** (mediante la conversión a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C:: Cree un AsyncPackage:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Convertir un VSPackage existente en AsyncPackage
 La mayor parte del trabajo es lo mismo que crear un nuevo **AsyncPackage**. Siga los pasos del 1 al 5 anteriores. También debe tener más cuidado con las siguientes recomendaciones:

1. Recuerde quitar `Initialize` la anulación que tenía en el paquete.

2. Evitar interbloqueos: podría haber RPC ocultos en el código. que ahora suceden en un hilo en segundo plano. Asegúrese de que si va a realizar un RPC (por ejemplo, **GetService**), debe (1) cambiar al subproceso principal o (2) usar la versión asincrónica de la API si existe (por ejemplo, **GetServiceAsync**).

3. No cambie entre roscas con demasiada frecuencia. Intente localizar el trabajo que puede ocurrir en un subproceso en segundo plano para reducir el tiempo de carga.

## <a name="querying-services-from-asyncpackage"></a>Consulta de servicios desde AsyncPackage
 Un **AsyncPackage** puede o no cargar de forma asincrónica dependiendo del llamador. Por ejemplo,

- Si el autor de la llamada llamó **a GetService** o **QueryService** (ambas API sincrónicas) o

- Si el llamador llamó **a IVsShell::LoadPackage** (o **IVsShell5::LoadPackageWithContext**) o

- La carga se desencadena mediante un contexto de interfaz de usuario, pero no se especificó que el mecanismo de contexto de interfaz de usuario puede cargar de forma asincrónica

  a continuación, el paquete se cargará sincrónicamente.

  El paquete todavía tiene una oportunidad (en su fase de inicialización asincrónica) para realizar el trabajo fuera del subproceso de interfaz de usuario, aunque el subproceso de interfaz de usuario se bloqueará para la finalización de ese trabajo. Si el autor de la llamada usa **IAsyncServiceProvider** para consultar de forma asincrónica el servicio, la carga y la inicialización se realizarán de forma asincrónica suponiendo que no se bloqueen inmediatamente en el objeto de tarea resultante.

  C: Cómo consultar el servicio de forma asincrónica:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```

---
title: Usar AsyncPackage para cargar VSPackages en segundo plano
description: Obtenga información sobre cómo usar la clase AsyncPackage que habilita la carga de paquetes en un subproceso en segundo plano, lo que puede impedir problemas de capacidad de respuesta de e/s de disco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: e8b5917a42e7083f7357ce76762bf8b51a1b60f9
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993489"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Cómo: usar AsyncPackage para cargar VSPackages en segundo plano
La carga e inicialización de un paquete de VS puede dar lugar a e/s de disco. Si dicha e/s se produce en el subproceso de la interfaz de usuario, puede provocar problemas de capacidad de respuesta. Para solucionar este tema, Visual Studio 2015 presentó la  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> clase que habilita la carga de paquetes en un subproceso en segundo plano.

## <a name="create-an-asyncpackage"></a>Creación de un AsyncPackage
 Puede empezar por crear un proyecto VSIX (**archivo**  >  **nuevo**  >  **proyecto** de  >  **Visual C#**  >  **extensibilidad**  >  **VSIX Project**) y agregando un VSPackage al proyecto (haga clic con el botón derecho en el proyecto y **agregue**  >  **nuevo elemento**  >  **C#**  >  **extensibilidad**  >  **Visual Studio Package**). Después, puede crear los servicios y agregarlos al paquete.

1. Derive el paquete de <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .

2. Si va a proporcionar servicios cuya consulta puede hacer que el paquete se cargue:

    Para indicar a Visual Studio que el paquete es seguro para la carga en segundo plano y para participar en este comportamiento, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> debe establecer la propiedad **AllowsBackgroundLoading** en true en el constructor de atributos.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Para indicar a Visual Studio que es seguro crear una instancia del servicio en un subproceso en segundo plano, debe establecer la <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> propiedad en true en el <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> constructor.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Si va a cargar a través de contextos de la interfaz de usuario, debe especificar **PackageAutoLoadFlags. BackgroundLoad** para <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o el valor (0X2) en las marcas escritas como el valor de la entrada de carga automática del paquete.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Si tiene trabajo de inicialización asincrónica, debe invalidar <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Quite el `Initialize()` método proporcionado por la plantilla VSIX. (El `Initialize()` método en **AsyncPackage** está sellado). Puede usar cualquiera de los <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> métodos para agregar servicios asincrónicos al paquete.

    Nota: para llamar a `base.InitializeAsync()` , puede cambiar el código fuente a:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Debe tener cuidado de no realizar RPC (llamada a procedimiento remoto) desde el código de inicialización asincrónico (en **InitializeAsync**). Esto puede ocurrir cuando se llama a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> directa o indirectamente.  Cuando se requieren cargas de sincronización, el subproceso de la interfaz de usuario se bloqueará mediante <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . El modelo de bloqueo predeterminado deshabilita las RPC. Esto significa que, si intenta usar una RPC de las tareas asincrónicas, se interbloqueará si el subproceso de la interfaz de usuario está esperando a que se cargue el paquete. La alternativa general es serializar el código en el subproceso de la interfaz de usuario, si es necesario, mediante algo como el **generador de tareas** que se puede unir <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o algún otro mecanismo que no usa una RPC.  No use **ThreadHelper. Generic. Invoke** o bloquee normalmente el subproceso de llamada en espera para llegar al subproceso de la interfaz de usuario.

    Nota: debe evitar el uso de **GetService** o **QueryService** en el `InitializeAsync` método. Si tiene que usarlos, deberá cambiar primero al subproceso de la interfaz de usuario. La alternativa es usar <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> desde **AsyncPackage** (convirtiéndolo en <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> ).

   C#: creación de un AsyncPackage:

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
 La mayor parte del trabajo es el mismo que la creación de un nuevo **AsyncPackage**. Siga los pasos del 1 al 5 anteriores. También debe tener especial precaución con las siguientes recomendaciones:

1. No olvide quitar la `Initialize` invalidación que tenía en el paquete.

2. Evite los interbloqueos: podría haber RPC ocultas en el código. que ahora se producen en un subproceso en segundo plano. Asegúrese de que si está creando una RPC (por ejemplo, **GetService**), debe (1) cambiar al subproceso principal o (2) usar la versión asincrónica de la API si existe una (por ejemplo, **GetServiceAsync**).

3. No cambie entre subprocesos con demasiada frecuencia. Intente localizar el trabajo que puede producirse en un subproceso en segundo plano para reducir el tiempo de carga.

## <a name="querying-services-from-asyncpackage"></a>Consultar servicios desde AsyncPackage
 Un **AsyncPackage** puede no cargarse de forma asincrónica dependiendo del llamador. Por ejemplo,

- Si el llamador llama a **GetService** o **QueryService** (ambas API sincrónicas) o

- Si el llamador llamó a **IVsShell:: LoadPackage** (o **IVsShell5:: LoadPackageWithContext**) o

- La carga se desencadena mediante un contexto de la interfaz de usuario, pero no especificó que el mecanismo de contexto de la interfaz de usuario pueda cargarse de forma asincrónica

  después, el paquete se cargará sincrónicamente.

  El paquete todavía tiene una oportunidad (en su fase de inicialización asincrónica) para trabajar fuera del subproceso de la interfaz de usuario, aunque el subproceso de la interfaz de usuario se bloqueará para la finalización de ese trabajo. Si el autor de la llamada usa **IAsyncServiceProvider** para consultar el servicio de forma asincrónica, la carga y la inicialización se realizarán de forma asincrónica suponiendo que no se bloqueen inmediatamente en el objeto de tarea resultante.

  C#: Cómo consultar el servicio de forma asincrónica:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```

---
title: Administrar la implementación especializada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploying applications [Visual Studio SDK]
- specialized deployment
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c54b98c7bc7341a09fee9e6e5d0cc6860f4254f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848958"
---
# <a name="handle-specialized-deployment"></a>Administrar la implementación especializada
Una implementación es una operación opcional para los proyectos de. Un proyecto Web, por ejemplo, admite una implementación para permitir que un proyecto actualice un servidor Web. Del mismo modo, un proyecto de **Smart Device** admite una implementación para copiar una aplicación compilada en el dispositivo de destino. Los subtipos de proyecto pueden proporcionar un comportamiento de implementación especializado implementando la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>. Esta interfaz define un conjunto completo de las operaciones de implementación:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>

  La operación de implementación real debe realizarse en el subproceso independiente para hacer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mayor capacidad de respuesta a la interacción del usuario. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llama a los métodos proporcionados por <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> de forma asincrónica y operan en segundo plano, lo que permite al entorno consultar el estado de una operación de implementación en cualquier momento o detener la operación, si es necesario. El entorno llama a las operaciones de implementación de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> cuando el usuario selecciona el comando implementar.

  Para notificar al entorno que una operación de implementación ha comenzado o finalizado, el subtipo de proyecto debe llamar a los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A>.

## <a name="to-handle-a-specialized-deployment-by-a-subtype-project"></a>Para controlar una implementación especializada mediante un proyecto de subtipo

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A> para registrar el entorno para recibir notificaciones de los eventos de estado de implementación.

    ```vb
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _
                                               ByRef pdwCookie As UInteger) As Integer

        If pIVsDeployStatusCallback Is Nothing Then
            Throw New ArgumentNullException("pIVsDeployStatusCallback")
        End If

        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)
        Return VSConstants.S_OK

    End Function
    ```

    ```csharp
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,
                                          out uint pdwCookie)
    {
        if (pIVsDeployStatusCallback == null)
            throw new ArgumentNullException("pIVsDeployStatusCallback");

        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);
        return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A> para cancelar el registro del entorno para recibir notificaciones de los eventos de estado de implementación.

    ```vb
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer
        adviseSink.RemoveAt(dwCookie)
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int UnadviseDeployStatusCallback(uint dwCookie)
    {
        adviseSink.RemoveAt(dwCookie);
        return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A> para realizar la operación de confirmación específica de la aplicación.  Este método se usa principalmente para la implementación de bases de datos.

    ```vb
    Public Function Commit(ByVal dwReserved As UInteger) As Integer
        'Implement commit operation here.
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int Commit(uint dwReserved)
    {
         //Implement commit operation here.
         return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A> para realizar una operación de reversión. Cuando se llama a este método, el proyecto de implementación debe hacer lo que sea adecuado para revertir los cambios y restaurar el estado del proyecto. Este método se usa principalmente para la implementación de bases de datos.

    ```vb
    Public Function Commit(ByVal dwReserved As UInteger) As Integer
        'Implement commit operation here.
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int Rollback(uint dwReserved)
    {
        //Implement Rollback operation here.
        return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A> para determinar si un proyecto puede iniciar una operación de implementación.

    ```vb
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then
            pfSupported(0) = 1
        End If
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then
            pfReady(0) = 0
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then
                pfReady(0) = 1
            End If
        End If
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)
    {
        if (pfSupported != null && pfSupported.Length >0)
            pfSupported[0] = 1;
        if (pfReady != null && pfReady.Length >0)
        {
            pfReady[0] = 0;
            if (deploymentThread != null && !deploymentThread.IsAlive)
                pfReady[0] = 1;
        }
        return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A> para determinar si una operación de implementación se ha completado correctamente.

    ```vb
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer
        pfDeployDone = 1
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            pfDeployDone = 0
        End If
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int QueryStatusDeploy(out int pfDeployDone)
    {
        pfDeployDone = 1;
        if (deploymentThread != null && deploymentThread.IsAlive)
            pfDeployDone = 0;
        return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A> para iniciar una operación de implementación en un subproceso independiente. Coloque el código específico de la implementación de la aplicación dentro del método `Deploy`.

    ```vb
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer
        If pIVsOutputWindowPane Is Nothing Then
            Throw New ArgumentNullException("pIVsOutputWindowPane")
        End If

        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")
        End If

        outputWindow = pIVsOutputWindowPane

        ' Notify that deployment is about to begin and see if any user wants to cancel.
        If (Not NotifyStart()) Then
            Return VSConstants.E_ABORT
        End If

        operationCanceled = False

        ' Create and start our thread
        deploymentThread = New Thread(AddressOf Me.Deploy)
        deploymentThread.Name = "Deployment Thread"
        deploymentThread.Start()

        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)
    {
        if (pIVsOutputWindowPane == null)
            throw new ArgumentNullException("pIVsOutputWindowPane");

        if (deploymentThread != null && deploymentThread.IsAlive)
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");

        outputWindow = pIVsOutputWindowPane;

        // Notify that deployment is about to begin and see if any user wants to cancel.
        if (!NotifyStart())
            return VSConstants.E_ABORT;

        operationCanceled = false;

        // Create and start our thread
        deploymentThread = new Thread(new ThreadStart(this.Deploy));
        deploymentThread.Name = "Deployment Thread";
        deploymentThread.Start();

        return VSConstants.S_OK;
    }

    ```

- Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A> para detener una operación de implementación. Se llama a este método cuando un usuario presiona el botón **Cancelar** durante el proceso de implementación.

    ```vb
    Public Function StopDeploy(ByVal fSync As Integer) As Integer
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            Return VSConstants.S_OK
        End If

        outputWindow.OutputStringThreadSafe("Canceling deployment")
        operationCanceled = True
        If fSync <> 0 Then
            ' Synchronous request, wait for the thread to terminate.
            If (Not deploymentThread.Join(10000)) Then
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")
                deploymentThread.Abort()
            End If
        End If

        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int StopDeploy(int fSync)
    {
        if (deploymentThread != null && deploymentThread.IsAlive)
            return VSConstants.S_OK;

        outputWindow.OutputStringThreadSafe("Canceling deployment");
        operationCanceled = true;
        if (fSync != 0)
        {
            // Synchronous request, wait for the thread to terminate.
            if (!deploymentThread.Join(10000))
            {
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");
                deploymentThread.Abort();
            }
        }

        return VSConstants.S_OK;
    }

    ```

> [!NOTE]
> Todos los ejemplos de código que se proporcionan en este tema son partes de un ejemplo más extenso en [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vea también
- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

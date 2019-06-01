---
title: Preguntas frecuentes sobre depuración de instantáneas | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43b76ad81a2c075a11ff55dcbd7fbc5e8a4b3fe7
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431844"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Preguntas frecuentes sobre depuración de instantáneas en Visual Studio

Aquí se muestra una lista de preguntas que pueden surgir al depurar aplicaciones de Azure en vivo con Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>¿Cuál es el costo de rendimiento de la realización de una instantánea?

Cuando Snapshot Debugger captura una instantánea de la aplicación, bifurca el proceso de la aplicación y suspende la copia bifurcada. Al depurar una instantánea, realmente se realiza la depuración de la copia bifurcada del proceso. Este proceso tarda solo entre 10 y 20 milisegundos, pero no copia el montón completo de la aplicación. En su lugar, copia solo la tabla de páginas y establece las páginas para la copia en escritura. Si algunos de los objetos del montón de la aplicación cambian, entonces se copian sus páginas correspondientes. De esa forma, cada instantánea tiene un costo reducido en memoria (del orden de cientos de kilobytes para la mayoría de las aplicaciones).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>¿Qué ocurre si tengo una instancia de Azure App Service de escalabilidad horizontal (varias instancias de mi aplicación)?

Si tiene varias instancias de la aplicación, los puntos de instantánea se aplican a cada instancia de forma individual. Solo el primer punto de instantánea que se alcanza con las condiciones especificadas crea una instantánea. Si tiene varios puntos de instantánea, las instantáneas posteriores proceden de la misma instancia que creó la primera instantánea. Los puntos de registro enviados a la ventana de salida solo mostrarán los mensajes de una instancia, mientras que los puntos de registro enviados a los registros de aplicaciones envían mensajes desde cada instancia.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>¿Cómo Snapshot Debugger carga los símbolos?

Snapshot Debugger requiere disponer de los símbolos correspondientes para la aplicación ya sea en el entorno local o implementados en Azure App Service. (Los archivos PDB insertados no son compatibles actualmente). Snapshot Debugger descarga los símbolos automáticamente de Azure App Service. A partir de Visual Studio 2017, versión 15.2, la implementación en Azure App Service también supone la implementación de los símbolos de la aplicación.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>¿Snapshot Debugger funciona con las compilaciones de versión de mi aplicación?

Sí; Snapshot Debugger está diseñado para funcionar con las compilaciones de versión. Cuando se coloca un punto de instantánea en una función, esta se vuelve a recompilar en una versión de depuración, de tal forma que se convierte en depurable. Al detener Snapshot Debugger, las funciones se devuelven a la versión de la compilación de versión.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>¿Los puntos de registro pueden causar efectos secundarios en mi aplicación de producción?

No; los mensajes de registro agregados a la aplicación se evalúan de forma práctica. No pueden causar ningún efecto secundario en la aplicación. Sin embargo, algunas propiedades nativas pueden no estar accesibles para los puntos de registro.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>¿Snapshot Debugger funciona si mi servidor está cargado?

Sí, la depuración de instantáneas puede funcionar en los servidores con carga. Snapshot Debugger limita y no captura las instantáneas en situaciones en las que hay una baja cantidad de memoria disponible en el servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>¿Cómo se puede desinstalar Snapshot Debugger?

Puede desinstalar la extensión de sitio de Snapshot Debugger en la instancia de App Service con estos pasos:

1. Desactivar el servicio de aplicaciones a través de Cloud Explorer en Visual Studio o el portal de Azure.
1. Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a **Extensiones de sitio**.
1. Haga clic en la X de la extensión de sitio de Snapshot Debugger para quitarla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>¿Por qué hay puertos abiertos durante una sesión de Snapshot Debugger?

Snapshot Debugger necesita abrir un conjunto de puertos para depurar las instantáneas realizadas en Azure; se trata de los mismos puertos necesarios para la depuración remota. [Puede encontrar la lista de puertos aquí](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>¿Cómo se puede deshabilitar la extensión del depurador remoto?

Para los servicios de aplicación:
1. Deshabilitar la extensión del depurador remoto a través del portal de Azure para App Service.
2. Azure portal > la hoja de recursos de servicio de aplicación > *configuración de la aplicación*
3. Navegue hasta la *depuración* sección y haga clic en el *desactivar* botón *depuración remota*.

Para AKS:
1. Actualizar el Dockerfile para quitar las secciones correspondientes a la [Visual Studio Snapshot Debugger en imágenes de Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile y vuelva a implementar la imagen de Docker.

Escalado de máquinas virtuales o máquinas virtuales conjuntos de quitar los grupos de KeyVaults y NAT de entrada de extensión, certificados, depurador remoto como sigue:

1. Quitar la extensión del depurador remoto  

   Hay varias formas de deshabilitar al depurador remoto para máquinas virtuales y conjuntos de escalado de máquinas virtuales:  

      - Deshabilitar al depurador remoto a través del explorador en la nube  

         - Cloud Explorer > recurso de máquina virtual > deshabilitar la depuración (deshabilitar la depuración no existe para el escalado de máquinas virtuales que se establezca en Cloud Explorer).  


      - Deshabilitar al depurador remoto con las secuencias de comandos y Cmdlets de PowerShell  

         Para la máquina virtual:  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Para conjuntos de escalado de máquinas virtuales:  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Deshabilitar al depurador remoto a través del portal de Azure
         - Azure portal > su máquina virtual/virtual machine scale sets con hoja de recursos > extensiones  
         - Desinstalar extensión Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  


         > [!NOTE]
         > Conjuntos de escalado de máquina virtual: el portal no permite quitar los puertos DebuggerListener. Deberá usar Azure PowerShell. Para obtener información más detallada, vea a continuación.
  
2. Quite los certificados y Azure Key Vault

   Al instalar la extensión del depurador remoto para máquina virtual o conjuntos de escalado de máquinas virtuales, se crean los certificados de cliente y servidor para autenticar al cliente de VS con la máquina Virtual de Azure/recursos de conjuntos de escalado de máquina virtual.  

   - El certificado de cliente  

      Este certificado es un certificado autofirmado ubicado en Cert: / CurrentUser/mi /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      Es una manera de eliminar este certificado desde el equipo a través de PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - El certificado de servidor
      - La huella digital del certificado de servidor correspondiente se implementa como un secreto a Azure Key Vault. VS intentará encontrar o crear un almacén de claves con el prefijo MSVSAZ * en la región que corresponde a la máquina virtual o recurso de conjuntos de escalado de máquina virtual. Conjuntos de escalado de máquina virtual o máquina virtual todos los recursos implementados en esa región, por tanto, compartirán el mismo almacén de claves.  
      - Para eliminar el secreto de huella digital del certificado de servidor, vaya a Azure portal y busque el almacén de claves MSVSAZ * en la misma región que hospeda el recurso. Eliminación del secreto que debe etiquetarse. `remotedebugcert<<ResourceName>>`  
      - También deberá eliminar el secreto de servidor desde el recurso a través de PowerShell.  

      Las máquinas virtuales:  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Para conjuntos de escalado de máquinas virtuales:  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Quitar todos los grupos de NAT de entrada DebuggerListener (sólo al conjunto de escalado de máquinas virtuales)  

   El depurador remoto presenta DebuggerListener en enlazados a los grupos NAT que se aplican al equilibrador de carga de su conjunto de escalado.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>¿Cómo deshabilitar el depurador de instantáneas?

Para App Service:
1. Deshabilitar el depurador de instantáneas a través del portal de Azure para App Service.
2. Azure portal > la hoja de recursos de servicio de aplicación > *configuración de la aplicación*
3. Elimine las siguientes opciones de la aplicación en Azure portal y guardar los cambios. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Los cambios realizados en la configuración de la aplicación iniciarán un reinicio de la aplicación. Puede encontrar detalles sobre la configuración de la aplicación [aquí](https://docs.microsoft.com/azure/app-service/web-sites-configure#app-settings). 

Para AKS:
1. Actualizar el Dockerfile para quitar las secciones correspondientes a la [Visual Studio Snapshot Debugger en imágenes de Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile y vuelva a implementar la imagen de Docker.

Para conjuntos de escalado de máquina virtual o máquina virtual:

Hay varias formas de deshabilitar al depurador de instantáneas:
- En la nube explorador > recurso de conjunto de la escala de máquina virtual/máquina virtual > Deshabilitar diagnósticos

- Azure portal > hoja de recursos de conjunto de la escala de máquina virtual/máquina virtual > Extensiones > Microsoft.Insights.VMDiagnosticsSettings Desinstalar extensión

- Cmdlets de PowerShell desde [Az PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Máquina virtual:
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    Conjuntos de escalado de máquinas virtuales:
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.md)
- [Depurar aplicaciones ASP.NET activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md)
- [Depurar conjuntos de escalado de ASP.NET Azure Virtual Machines de Machines\Virtual en vivo mediante el depurador de instantáneas](../debugger/debug-live-azure-virtual-machines.md)
- [Depuración en directo ASP.NET Azure Kubernetes con el depurador de instantáneas](../debugger/debug-live-azure-kubernetes.md)
- [Problemas conocidos y solución de problemas de depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md)
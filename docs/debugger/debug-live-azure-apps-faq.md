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
ms.openlocfilehash: ceda2dd4e85c8db5b66ef753a748977204b8caab
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211217"
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

1. Desactive el App Service a través del Cloud Explorer en Visual Studio o en el Azure Portal.
1. Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a **Extensiones de sitio**.
1. Haga clic en la X de la extensión de sitio de Snapshot Debugger para quitarla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>¿Por qué hay puertos abiertos durante una sesión de Snapshot Debugger?

Snapshot Debugger necesita abrir un conjunto de puertos para depurar las instantáneas realizadas en Azure; se trata de los mismos puertos necesarios para la depuración remota. [Puede encontrar la lista de puertos aquí](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>¿Cómo deshabilitar la extensión del Depurador remoto?

Por App Services:
1. Deshabilite la extensión del Depurador remoto a través del Azure Portal para el App Service.
2. Azure Portal > la hoja de recursos del servicio de aplicación > la configuración de la *aplicación*
3. Navegue hasta la sección *depuración* y haga clic en el botón *desactivado* para *depuración remota*.

Para AKS:
1. Actualice el Dockerfile para quitar las secciones correspondientes al [Visual Studio Snapshot Debugger en las imágenes de Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile y vuelva a implementar la imagen de Docker modificada.

En el caso de los conjuntos de escalado de máquinas virtuales o máquinas virtuales, quite la extensión del Depurador remoto, los certificados, los grupos de KeyVaults y NAT de entrada como se indica a continuación:

1. Quitar la extensión del Depurador remoto

   Hay varias maneras de deshabilitar el depurador remoto para máquinas virtuales y conjuntos de escalado de máquinas virtuales:

      - Deshabilite el depurador remoto a través de Cloud Explorer

         - Cloud Explorer > el recurso de máquina virtual > deshabilitar la depuración (no existe la deshabilitación de la depuración para el conjunto de escalado de máquinas virtuales en Cloud Explorer).

      - Deshabilitar el depurador remoto con scripts o cmdlets de PowerShell

         Para la máquina virtual:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Para conjuntos de escalado de máquinas virtuales:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Deshabilite el depurador remoto a través del Azure Portal
         - Azure Portal > la hoja de recursos de máquinas virtuales o conjuntos de escalado de máquinas virtuales > extensiones
         - Desinstalar la extensión Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Conjuntos de escalado de máquinas virtuales: el portal no permite la eliminación de los puertos DebuggerListener. Tendrá que utilizar Azure PowerShell. Para obtener información más detallada, vea a continuación.

2. Quitar certificados y Azure KeyVault

   Al instalar la extensión del Depurador remoto para máquinas virtuales o conjuntos de escalado de máquinas virtuales, se crean certificados de cliente y de servidor para autenticar el cliente de VS con los recursos de la máquina virtual de Azure o de los conjuntos de escalado de máquinas virtuales.

   - El certificado de cliente

      Este certificado es un certificado autofirmado que se encuentra en CERT:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Una manera de quitar este certificado de la máquina es a través de PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - El certificado de servidor
      - La huella digital del certificado de servidor correspondiente se implementa como un secreto en Azure KeyVault. VS tratará de buscar o crear un KeyVault con el prefijo MSVSAZ * en la región correspondiente a la máquina virtual o al recurso de conjuntos de escalado de máquinas virtuales. Por lo tanto, todos los recursos de máquinas virtuales o conjuntos de escalado de máquinas virtuales implementados en esa región compartirán el mismo KeyVault.
      - Para eliminar el secreto de huella digital del certificado de servidor, vaya al Azure Portal y busque el MSVSAZ * KeyVault en la misma región que hospeda el recurso. Eliminar el secreto que se debe etiquetar`remotedebugcert<<ResourceName>>`
      - También tendrá que eliminar el secreto de servidor del recurso a través de PowerShell.

      Para las máquinas virtuales:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Para conjuntos de escalado de máquinas virtuales:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Quitar todos los grupos NAT de entrada de DebuggerListener (solo en el conjunto de escalado de máquinas virtuales)

   El depurador remoto introduce grupos NAT enlazados a DebuggerListener que se aplican al equilibrador de carga de escalado.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>¿Cómo deshabilitar Snapshot Debugger?

Por App Service:
1. Deshabilite Snapshot Debugger a través del Azure Portal para el App Service.
2. Azure Portal > la hoja de recursos del servicio de aplicación > la configuración de la *aplicación*
3. Elimine la siguiente configuración de la aplicación en el Azure Portal y guarde los cambios.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Cualquier cambio en la configuración de la aplicación iniciará un reinicio de la aplicación. Para obtener más información sobre la configuración de la aplicación, consulte [configuración de una aplicación App Service en el Azure portal](/azure/app-service/web-sites-configure).

Para AKS:
1. Actualice el Dockerfile para quitar las secciones correspondientes al [Visual Studio Snapshot Debugger en las imágenes de Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile y vuelva a implementar la imagen de Docker modificada.

Para máquinas virtuales o conjuntos de escalado de máquinas virtuales:

Hay varias maneras de deshabilitar el Snapshot Debugger:
- Cloud Explorer > el recurso del conjunto de escalado de máquinas virtuales o máquinas virtuales > deshabilitar los diagnósticos

- Azure Portal > la hoja de recursos del conjunto de escalado de máquinas virtuales o máquinas virtuales > Extensiones > desinstalar la extensión Microsoft. Insights. VMDiagnosticsSettings

- Cmdlets de PowerShell de [AZ PowerShell](https://docs.microsoft.com/powershell/azure/overview)

   Máquina virtual:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Conjuntos de escalado de máquinas virtuales:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Depure aplicaciones de ASP.NET dinámicas con el Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Depure conjuntos de escalado de máquinas virtuales de Azure virtual Machines\Virtual ASP.NET con el Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Depure Live ASP.NET Azure Kubernetes mediante el Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Solución de problemas y problemas conocidos de la depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md)

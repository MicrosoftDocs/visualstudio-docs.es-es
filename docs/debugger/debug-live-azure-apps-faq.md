---
title: Preguntas frecuentes sobre depuración de instantáneas | Microsoft Docs
description: Revise una lista de las preguntas más frecuentes (P+F) que pueden surgir al depurar aplicaciones de Azure activas con Snapshot Debugger en Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5276127f0d6755b9fdabdfa965b5c1b8c4d94823
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727208"
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

1. Desactive la instancia de App Service en Cloud Explorer en Visual Studio o en Azure Portal.
1. Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a **Extensiones de sitio**.
1. Haga clic en la X de la extensión de sitio de Snapshot Debugger para quitarla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>¿Por qué hay puertos abiertos durante una sesión de Snapshot Debugger?

Snapshot Debugger necesita abrir un conjunto de puertos para depurar las instantáneas realizadas en Azure; se trata de los mismos puertos necesarios para la depuración remota. [Puede encontrar la lista de puertos aquí](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>¿Cómo se deshabilita la extensión de Remote Debugger?

Para App Services:
1. Deshabilite la extensión de Remote Debugger a través de Azure Portal para la instancia de App Service.
2. Azure Portal > hoja del recurso del servicio de aplicación > *Configuración de la aplicación*
3. Vaya a la sección *Depuración* y haga clic en el botón *Off* (Desactivar) para la *Depuración remota*.

Para AKS:
1. Actualice el Dockerfile para quitar las secciones que corresponden a [Visual Studio Snapshot Debugger en las imágenes de Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile y vuelva a implementar la imagen de Docker modificada.

En Virtual Machine/Virtual Machine Scale Sets, quite la extensión de Remote Debugger, los certificados, los almacenes de claves y los grupos NAT de entrada como se indica a continuación:

1. Eliminación de la extensión de Remote Debugger

   Hay varias maneras de deshabilitar Remote Debugger para Virtual Machine/Virtual Machine Scale Sets:

      - Deshabilite Remote Debugger a través de Cloud Explorer

         - Cloud Explorer > el recurso de la máquina virtual > Deshabilitar depuración (la deshabilitación de la depuración no existe para Virtual Machine Scale Sets en Cloud Explorer).

      - Deshabilite Remote Debugger con scripts/cmdlets de PowerShell

         Para la máquina virtual:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Para los conjuntos de escalado de máquinas virtuales:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Deshabilite Remote Debugger a través de Azure Portal
         - Azure Portal > hoja del recurso de Virtual Machine/Virtual Machine Scale Sets > Extensiones
         - Desinstale la extensión Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger

         > [!NOTE]
         > Virtual Machine Scale Sets: el portal no permite quitar los puertos DebuggerListener. Tendrá que usar Azure PowerShell. Para obtener información más detallada, vea a continuación.

2. Eliminación de certificados y Azure KeyVault

   Al instalar la extensión de Remote Debugger para Virtual Machine/Virtual Machine Scale Sets, se crean certificados de cliente y servidor para autenticar el cliente de Visual Studio con los recursos de Azure Virtual Machine/Virtual Machine Scale Sets.

   - El certificado de cliente

      Este certificado es un certificado autofirmado ubicado en Cert:/CurrentUser/My/

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
      - La huella digital del certificado de servidor correspondiente se implementa como un secreto en Azure KeyVault. Visual Studio intentará encontrar o crear una instancia de KeyVault con el prefijo MSVSAZ* en la región correspondiente al recurso de Virtual Machine/Virtual Machine Scale Sets. Por lo tanto, todos los recursos de Virtual Machine/Virtual Machine Scale Sets implementados en esa región compartirán la misma instancia de KeyVault.
      - Para eliminar el secreto de la huella digital del certificado de servidor, vaya a Azure Portal y busque la instancia de KeyVault MSVSAZ* en la misma región donde se hospeda el recurso. Elimine el secreto que debe tener la etiqueta `remotedebugcert<<ResourceName>>`
      - También deberá eliminar el secreto de servidor del recurso a través de PowerShell.

      Para las máquinas virtuales:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Para los conjuntos de escalado de máquinas virtuales:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Eliminación de todos los grupos NAT de entrada de DebuggerListener (solo en Virtual Machine Scale Sets)

   Remote Debugger introduce los grupos NAT de entrada DebuggerListener que se aplican al equilibrador de carga del conjunto de escalado.

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

#### <a name="how-do-i-disable-snapshot-debugger"></a>¿Cómo se deshabilita Snapshot Debugger?

Para App Service:
1. Deshabilite Snapshot Debugger a través de Azure Portal para su instancia de App Service.
2. Azure Portal > hoja del recurso del servicio de aplicación > *Configuración de la aplicación*
3. Elimine la siguiente configuración de la aplicación en Azure Portal y guarde los cambios.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Cualquier cambio en la configuración de la aplicación iniciará un reinicio de la aplicación. Para más información sobre la configuración de la aplicación, consulte [Configurar una aplicación de App Service en Azure Portal](/azure/app-service/web-sites-configure).

Para AKS:
1. Actualice el Dockerfile para quitar las secciones que corresponden a [Visual Studio Snapshot Debugger en las imágenes de Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Recompile y vuelva a implementar la imagen de Docker modificada.

Para Virtual Machine/Virtual Machine Scale Sets:

Hay varias maneras de deshabilitar Snapshot Debugger:
- Cloud Explorer > el recurso de Virtual Machine/Virtual Machine Scale Sets > Deshabilitar diagnósticos

- Azure Portal > hoja del recurso de Virtual Machine/Virtual Machine Scale Sets > Extensiones > Desinstalar la extensión Microsoft.Insights.VMDiagnosticsSettings

- Cmdlets de PowerShell de [Az PowerShell](/powershell/azure/overview)

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
- [Depuración de aplicaciones ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Depuración de aplicaciones ASP.NET en vivo en Azure Virtual Machines\Virtual Machines Scale Sets con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Depuración de Azure Kubernetes de ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Solución de problemas y problemas conocidos de depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md)

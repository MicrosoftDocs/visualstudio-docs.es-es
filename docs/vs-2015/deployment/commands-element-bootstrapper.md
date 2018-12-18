---
title: '&lt;Comandos&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 309f93658cee6663c2b5673c03c6621330e7fa39
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276580"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Comandos&gt; (elemento, arranque)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `Commands` elemento implementa las pruebas descritas por los elementos subyacentes el `InstallChecks` elemento y declara el paquete en el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] debe instalar el programa previo si se produce un error en la prueba.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `Commands` elemento es necesario. El elemento tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Reboot`|Opcional. Determina si el sistema debería reiniciar si cualquiera de los paquetes devuelve un código de salida de reinicio. La siguiente lista muestra los valores válidos:<br /><br /> `Defer`. El reinicio se aplaza hasta un momento posterior.<br /><br /> `Immediate`. Hace que un reinicio inmediato si uno de los paquetes devuelve un código de salida de reinicio.<br /><br /> `None`. Hace que las solicitudes de reinicio se pasará por alto.<br /><br /> De manera predeterminada, es `Immediate`.|  
  
## <a name="command"></a>Comando  
 El elemento `Command` es un elemento secundario del elemento `Commands`. Un `Commands` elemento puede tener uno o más `Command` elementos. El elemento tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`PackageFile`|Requerido. El nombre del paquete que instale debe una o varias de las condiciones especificadas por `InstallConditions` devuelva false. El paquete debe definirse en el mismo archivo utilizando un `PackageFile` elemento.|  
|`Arguments`|Opcional. Un conjunto de argumentos de línea de comandos para pasar el archivo de paquete.|  
|`EstimatedInstallSeconds`|Opcional. El tiempo estimado, en segundos, tendrá que para instalar el paquete. Este valor determina el tamaño de la barra de progreso que el programa previo muestra al usuario. El valor predeterminado es 0, en cuyo caso estimación se especifica ninguna horaria.|  
|`EstimatedDiskBytes`|Opcional. La cantidad estimada de espacio en disco, en bytes, que ocupará el paquete después de la instalación ha finalizado. Este valor se utiliza en los requisitos de espacio en disco duro que el programa previo muestra al usuario. El valor predeterminado es 0, en cuyo caso el programa previo no muestra ningún requisito de espacio de disco duro.|  
|`EstimatedTempBytes`|Opcional. La cantidad estimada de espacio en disco temporal, en bytes, que será necesario el paquete.|  
|`Log`|Opcional. La ruta de acceso al archivo de registro que genera el paquete, relativa al directorio raíz del paquete.|  
  
## <a name="installconditions"></a>InstallConditions  
 El `InstallConditions` es un elemento secundario de la `Command` elemento. Cada `Command` elemento puede tener como máximo un `InstallConditions` elemento. Si no hay ningún `InstallConditions` elemento existe, el paquete especificado por `Condition` siempre se ejecutará.  
  
## <a name="bypassif"></a>BypassIf  
 El `BypassIf` es un elemento secundario de la `InstallConditions` elemento y describe una condición positiva en la que no se debe ejecutar el comando. Cada `InstallConditions` elemento puede tener cero o más `BypassIf` elementos.  
  
 `BypassIf` tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad que se va a probar. La propiedad debe anteriormente se han definido por un elemento secundario de la `InstallChecks` elemento. Para obtener más información, consulte [ \<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Requerido. El tipo de comparación que se va a realizar. La siguiente lista muestra los valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Requerido. El valor que se compara con la propiedad.|  
|`Schedule`|Opcional. El nombre de un `Schedule` etiqueta que define cuándo se debe evaluar esta regla.|  
  
## <a name="failif"></a>FailIf  
 El `FailIf` es un elemento secundario de la `InstallConditions` elemento y describe una condición positiva en la que la instalación debe detenerse. Cada `InstallConditions` elemento puede tener cero o más `FailIf` elementos.  
  
 `FailIf` tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad que se va a probar. La propiedad debe anteriormente se han definido por un elemento secundario de la `InstallChecks` elemento. Para obtener más información, consulte [ \<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Requerido. El tipo de comparación que se va a realizar. La siguiente lista muestra los valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Requerido. El valor que se compara con la propiedad.|  
|`String`|Opcional. El texto que se muestra al usuario en caso de error.|  
|`Schedule`|Opcional. El nombre de un `Schedule` etiqueta que define cuándo se debe evaluar esta regla.|  
  
## <a name="exitcodes"></a>ExitCodes  
 El `ExitCodes` es un elemento secundario de la `Command` elemento. El `ExitCodes` elemento contiene uno o varios `ExitCode` elementos, que determinan lo que debe hacer la instalación en respuesta a un código de salida de un paquete. Puede haber uno opcional `ExitCode` elemento debajo de un `Command` elemento. `ExitCodes` no tiene atributos.  
  
## <a name="exitcode"></a>ExitCode  
 El `ExitCode` es un elemento secundario de la `ExitCodes` elemento. El `ExitCode` elemento determina lo que debe hacer la instalación en respuesta a un código de salida de un paquete. `ExitCode` no contiene elementos secundarios y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Value`|Requerido. El valor del código de salida a la que se `ExitCode` se aplica el elemento.|  
|`Result`|Requerido. Cómo la instalación debe reaccionar a este código de salida. La siguiente lista muestra los valores válidos:<br /><br /> `Success`. Indica que el paquete ha instalado correctamente.<br /><br /> `SuccessReboot`. Indica que el paquete ha instalado correctamente e indica el reinicio del sistema.<br /><br /> `Fail`. Marca el paquete como erróneo.<br /><br /> `FailReboot`. Marca el paquete como erróneo e indica el reinicio del sistema.|  
|`String`|Opcional. El valor para mostrar al usuario en respuesta a este código de salida.|  
|`FormatMessageFromSystem`|Opcional. Determina si se debe usar el mensaje de error proporcionado por el sistema correspondiente al código de salida, o usar el valor proporcionado en `String`. Los valores válidos son `true`, lo que significa utilizar el error proporcionado por el sistema, y `false`, lo que significa utilizar la cadena proporcionada por `String`. De manera predeterminada, es `false`. Si esta propiedad es `false`, pero `String` no está establecido, se usará el error proporcionado por el sistema.|  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código define los comandos para instalar .NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de paquete y producto](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > elemento](../deployment/installchecks-element-bootstrapper.md)




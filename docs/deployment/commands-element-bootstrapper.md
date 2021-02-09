---
title: '&lt;Elemento Commands &gt; (arranque) | Microsoft Docs'
description: El elemento Commands implementa las pruebas en los elementos bajo InstallChecks y declara el paquete que se va a instalar si se produce un error en la prueba del programa previo ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f53ca683e40be8e3cc428d013d2b8d3c8c5773e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881235"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Elemento Commands &gt; (arranque)
El `Commands` elemento implementa las pruebas descritas por los elementos situados debajo del `InstallChecks` elemento y declara qué paquete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] debe instalar el programa previo si se produce un error en la prueba.

## <a name="syntax"></a>Sintaxis

```xml
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
 El elemento `Commands` es obligatorio. El elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Reboot`|Opcional. Determina si el sistema debe reiniciarse si alguno de los paquetes devuelve un código de salida de reinicio. En la lista siguiente se muestran los valores válidos:<br /><br /> `Defer`. El reinicio se aplaza hasta un momento posterior.<br /><br /> `Immediate`. Provoca un reinicio inmediato si uno de los paquetes devuelve un código de salida de reinicio.<br /><br /> `None`. Hace que se omitan las solicitudes de reinicio.<br /><br /> De manera predeterminada, es `Immediate`.|

## <a name="command"></a>Comando
 El elemento `Command` es un elemento secundario del elemento `Commands`. Un `Commands` elemento puede tener uno o más `Command` elementos. El elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`PackageFile`|Necesario. Nombre del paquete que se va a instalar si una o varias de las condiciones especificadas por `InstallConditions` devuelven false. El paquete debe definirse en el mismo archivo mediante un `PackageFile` elemento.|
|`Arguments`|Opcional. Conjunto de argumentos de línea de comandos que se van a pasar al archivo de paquete.|
|`EstimatedInstallSeconds`|Opcional. El tiempo estimado, en segundos, que se tardará en instalar el paquete. Este valor determina el tamaño de la barra de progreso que el programa previo muestra al usuario. El valor predeterminado es 0, en cuyo caso no se especifica ninguna estimación de tiempo.|
|`EstimatedDiskBytes`|Opcional. Cantidad estimada de espacio en disco, en bytes, que el paquete ocupará una vez finalizada la instalación. Este valor se usa en los requisitos de espacio en disco duro que el programa previo muestra al usuario. El valor predeterminado es 0, en cuyo caso el programa previo no muestra ningún requisito de espacio en disco duro.|
|`EstimatedTempBytes`|Opcional. Cantidad estimada de espacio temporal en disco, en bytes, que necesitará el paquete.|
|`Log`|Opcional. La ruta de acceso al archivo de registro que genera el paquete, en relación con el directorio raíz del paquete.|

## <a name="installconditions"></a>InstallConditions
 El `InstallConditions` elemento es un elemento secundario del `Command` elemento. Cada `Command` elemento puede tener como máximo un `InstallConditions` elemento. Si no `InstallConditions` existe ningún elemento, el paquete especificado por `Condition` siempre se ejecutará.

## <a name="bypassif"></a>BypassIf
 El `BypassIf` elemento es un elemento secundario del `InstallConditions` elemento y describe una condición positiva en la que no se debe ejecutar el comando. Cada `InstallConditions` elemento puede tener cero o más `BypassIf` elementos.

 `BypassIf` tiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Necesario. Nombre de la propiedad que se va a comprobar. La propiedad debe haber sido definida previamente por un elemento secundario del `InstallChecks` elemento. Para obtener más información, consulte [Elemento \<InstallChecks>](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Necesario. Tipo de comparación que se va a realizar. En la lista siguiente se muestran los valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Necesario. Valor que se va a comparar con la propiedad.|
|`Schedule`|Opcional. El nombre de una `Schedule` etiqueta que define cuándo se debe evaluar esta regla.|

## <a name="failif"></a>FailIf
 El `FailIf` elemento es un elemento secundario del `InstallConditions` elemento y describe una condición positiva en la que debe detenerse la instalación. Cada `InstallConditions` elemento puede tener cero o más `FailIf` elementos.

 `FailIf` tiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Necesario. Nombre de la propiedad que se va a comprobar. La propiedad debe haber sido definida previamente por un elemento secundario del `InstallChecks` elemento. Para obtener más información, consulte [Elemento \<InstallChecks>](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Necesario. Tipo de comparación que se va a realizar. En la lista siguiente se muestran los valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Necesario. Valor que se va a comparar con la propiedad.|
|`String`|Opcional. Texto que se va a mostrar al usuario cuando se produzca un error.|
|`Schedule`|Opcional. El nombre de una `Schedule` etiqueta que define cuándo se debe evaluar esta regla.|

## <a name="exitcodes"></a>ExitCodes
 El `ExitCodes` elemento es un elemento secundario del `Command` elemento. El `ExitCodes` elemento contiene uno o más `ExitCode` elementos, que determinan lo que debe hacer la instalación en respuesta a un código de salida de un paquete. Puede haber un elemento opcional `ExitCode` debajo de un `Command` elemento. `ExitCodes` no tiene atributos.

## <a name="exitcode"></a>ExitCode
 El `ExitCode` elemento es un elemento secundario del `ExitCodes` elemento. El `ExitCode` elemento determina lo que debe hacer la instalación en respuesta a un código de salida de un paquete. `ExitCode` no contiene elementos secundarios y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Value`|Necesario. Valor del código de salida al que `ExitCode` se aplica este elemento.|
|`Result`|Necesario. Cómo debe responder la instalación a este código de salida. En la lista siguiente se muestran los valores válidos:<br /><br /> `Success`. Marca el paquete como instalado correctamente.<br /><br /> `SuccessReboot`. Marca el paquete como instalado correctamente e indica al sistema que se reinicie.<br /><br /> `Fail`. Marca el paquete como erróneo.<br /><br /> `FailReboot`. Marca el paquete como con errores y indica al sistema que se reinicie.|
|`String`|Opcional. Valor que se va a mostrar al usuario en respuesta a este código de salida.|
|`FormatMessageFromSystem`|Opcional. Determina si se debe usar el mensaje de error proporcionado por el sistema correspondiente al código de salida o el valor proporcionado en `String` . Los valores válidos son `true` , lo que significa que se debe usar el error proporcionado por el sistema, y `false` , que significa usar la cadena proporcionada por `String` . De manera predeterminada, es `false`. Si esta propiedad es `false` , pero `String` no se establece, se usará el error proporcionado por el sistema.|

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se definen comandos para instalar el .NET Framework 2,0.

```xml
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
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)
- [Elemento \<InstallChecks>](../deployment/installchecks-element-bootstrapper.md)
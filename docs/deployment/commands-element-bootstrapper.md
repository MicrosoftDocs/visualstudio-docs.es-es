---
title: "&lt;Commands&gt; (Elemento, Arranque) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Commands> (elemento) [arranque]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Commands&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento `Commands` implementa las pruebas descritas por los elementos subyacentes al elemento `InstallChecks`, y declara el paquete en el que el arranque de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deberá realizar la instalación en caso de que la prueba no se ejecute correctamente.  
  
## Sintaxis  
  
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
  
## Elementos y atributos  
 Se requiere el elemento `Commands`.  Este elemento tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Reboot`|Opcional.  Determina si el sistema debería reiniciar si cualquiera de los paquetes devuelve un código de salida del reinicio.  En la siguiente lista se muestran los valores válidos:<br /><br /> `Defer`.  El reinicio es diferido hasta un momento posterior.<br /><br /> `Immediate`.  Produce un reinicio inmediato si uno de los paquetes devuelve un código de salida del reinicio.<br /><br /> `None`.  Se pasará por alto cualquier solicitud de reinicio.<br /><br /> El valor predeterminado es `Immediate`.|  
  
## Command  
 El elemento `Command` es un elemento secundario del elemento `Commands`.  Un elemento `Commands` puede tener uno o más elementos `Command`.  El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`PackageFile`|Obligatorio.  El nombre del paquete que se instalará si una o más de las condiciones especificadas por `InstallConditions` devuelve falso.  El paquete debe definirse en el mismo archivo utilizando un elemento `PackageFile`.|  
|`Arguments`|Opcional.  Un conjunto de argumentos de la línea de comandos que se pasará al archivo de paquetes.|  
|`EstimatedInstallSeconds`|Opcional.  Tiempo estimado \(en segundos\) que se tardará en instalar el paquete.  Este valor determina el tamaño de la barra de progreso que el arranque muestra al usuario.  El valor predeterminado es 0, en cuyo caso no se especifica ninguna estimación de tiempo.|  
|`EstimatedDiskBytes`|Opcional.  Cantidad estimada de espacio en disco \(en bytes\) que ocupará el paquete una vez finalizada la instalación.  Este valor se utiliza en los requisitos de espacio en disco duro que el arranque muestra al usuario.  El valor predeterminado es 0, en cuyo caso el arranque no muestra ningún requisito de espacio en el disco duro.|  
|`EstimatedTempBytes`|Opcional.  La cantidad estimada de espacio en disco temporal, en bytes, que el paquete requerirá.|  
|`Log`|Opcional.  Ruta de acceso al archivo de registro generado por el paquete, relativa al directorio raíz del paquete.|  
  
## InstallConditions  
 El elemento `InstallConditions` es un elemento secundario del elemento `Command`.  Cada elemento `Command` puede tener al menos un elemento `InstallConditions`.  Si no existe ningún elemento `InstallConditions`, el paquete especificado por `Condition` se ejecutará siempre.  
  
## BypassIf  
 El elemento `BypassIf` es un elemento secundario del elemento `InstallConditions` y describe una condición positiva bajo la cual no se debería ejecutar el comando.  Cada elemento `InstallConditions` puede tener cero o más elementos `BypassIf`.  
  
 `BypassIf` tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que se va a comprobar.  La propiedad debe previamente estar definida por un elemento secundario del elemento `InstallChecks`.  Para obtener más información, vea [\<InstallChecks\> \(Elemento\)](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obligatorio.  El tipo de comparación que se va a realizar.  En la siguiente lista se muestran los valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obligatorio.  Valor que se va a comparar con la propiedad.|  
|`Schedule`|Opcional.  El nombre de una etiqueta `Schedule` que define cuándo se debería evaluar esta regla.|  
  
## FailIf  
 El elemento `FailIf` es un elemento secundario del elemento `InstallConditions` y describe una condición positiva bajo la cual la instalación debería detenerse.  Cada elemento `InstallConditions` puede tener cero o más elementos `FailIf`.  
  
 `FailIf` tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que se va a comprobar.  La propiedad debe previamente estar definida por un elemento secundario del elemento `InstallChecks`.  Para obtener más información, vea [\<InstallChecks\> \(Elemento\)](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obligatorio.  El tipo de comparación que se va a realizar.  En la siguiente lista se muestran los valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obligatorio.  Valor que se va a comparar con la propiedad.|  
|`String`|Opcional.  El texto que se mostrará al usuario cuando se produzca un error.|  
|`Schedule`|Opcional.  El nombre de una etiqueta `Schedule` que define cuándo se debería evaluar esta regla.|  
  
## ExitCodes  
 El elemento `ExitCodes` es un elemento secundario del elemento `Command`.  El elemento `ExitCodes` contiene uno o varios elementos `ExitCode`, que determinan lo que debe hacer la instalación en respuesta a un código de salida de un paquete.  Puede haber un elemento `ExitCode` opcional debajo de un elemento `Command`.  `ExitCodes` no tiene atributos.  
  
## ExitCode  
 El elemento `ExitCode` es un elemento secundario del elemento `ExitCodes`.  El elemento `ExitCode` determina lo que la instalación debe realizar en respuesta a un código de salida de un paquete.  `ExitCode` no contiene elementos secundarios y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Value`|Obligatorio.  El valor del código de salida al que se aplica este elemento `ExitCode`.|  
|`Result`|Obligatorio.  Cómo la instalación debe reaccionar a este código de salida.  En la siguiente lista se muestran los valores válidos:<br /><br /> `Success`.  Marca el paquete como correctamente instalado.<br /><br /> `SuccessReboot`.  Marca el paquete como correctamente instalado e indica al sistema que reinicie.<br /><br /> `Fail`.  Marca el paquete como erróneo.<br /><br /> `FailReboot`.  Marca el paquete como erróneo e indica al sistema que reinicie.|  
|`String`|Opcional.  El valor que se mostrará al usuario en respuesta a este código de salida.|  
|`FormatMessageFromSystem`|Opcional.  Determina si se utilizará el mensaje de error proporcionado por el sistema que corresponde al código de salida o si se utilizará el valor proporcionado en `String`.  Los valores válidos son `true`, que significa utilizar el error proporcionado por el sistema y `false`, que significa utilizar la cadena proporcionada por `String`.  El valor predeterminado es `false`.  Si esta propiedad es `false`, pero no se ha establecido `String`, se utilizará el error proporcionado por sistema.|  
  
## Ejemplo  
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
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks\> \(Elemento\)](../deployment/installchecks-element-bootstrapper.md)
---
title: Scripts de PowerShell para publicar en entornos de desarrollo y prueba
description: Aprenda a utilizar scripts de Windows PowerShell desde Visual Studio para publicar entornos de prueba y desarrollo.
author: ghogen
manager: jillfra
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 775c68b433073931f7f6a1b73fae89fcce6ca2b2
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916017"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Uso de scripts de Windows PowerShell para publicar en entornos de desarrollo y prueba

Al crear una aplicación web en Visual Studio, puede generar un script de Windows PowerShell que puede usar posteriormente para automatizar la publicación de su sitio Web en Azure como aplicación web en Azure App Service o una máquina virtual. Puede editar y ampliar el script de Windows PowerShell en el editor de Visual Studio para adaptarse a sus requisitos o integrar el script con los scripts de compilación, pruebas y publicación existentes.

Mediante estos scripts, puede aprovisionar versiones personalizadas (también conocidos como entornos de desarrollo y pruebas) de su sitio para uso temporal. Por ejemplo, podría configurar una versión concreta de su sitio web en una máquina virtual de Azure o en la ranura de ensayo de un sitio web para ejecutar un conjunto de pruebas, reproducir un error, probar una corrección de errores, realizar una versión de prueba de un cambio propuesto o configurar un entorno personalizado para una demo o presentación. Una vez creado un script que publique el proyecto, puede volver a crear entornos idénticos si vuelve a ejecutar el script según sea necesario, o ejecutar el script con su propia versión de la aplicación web para crear un entorno personalizado para pruebas.

## <a name="prerequisites"></a>Requisitos previos

* Visual Studio 2015 o posterior con la **carga de trabajo de Azure** instalada o Visual Studio 2013 y Azure SDK 2.3 o posterior. Vea las [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads). (No necesita Azure SDK para generar los scripts para proyectos web. Esta característica es para proyectos web, no para los roles web de Cloud Services).
* Azure PowerShell 0.7.4 o posterior. Consulte [Instalación y configuración de Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)) o posterior.

## <a name="additional-tools"></a>Herramientas adicionales

Tiene a su disposición herramientas y recursos adicionales para trabajar con PowerShell en Visual Studio para el desarrollo de Azure. Vea [Herramientas de PowerShell para Visual Studio](https://marketplace.visualstudio.com/items?itemName=AdamRDriscoll.PowerShellToolsforVisualStudio2015).

## <a name="generating-the-publish-scripts"></a>Generación de los scripts de publicación

Puede generar los scripts de publicación para una máquina virtual que hospeda el sitio web al crea un nuevo proyecto siguiendo [estas instrucciones](/azure/virtual-machines/windows/classic/web-app-visual-studio). También puede [generar scripts de publicación para aplicaciones web en Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Scripts que genera Visual Studio

Visual Studio genera una carpeta de nivel de solución denominada **PublishScripts** que contiene dos archivos de Windows PowerShell, un script de publicación para su máquina virtual o sitio web, y un módulo que contiene funciones que puede usar en los scripts. Visual Studio también genera un archivo en el formato JSON que especifica los detalles del proyecto que va a implementar.

### <a name="windows-powershell-publish-script"></a>Script de publicación de Windows PowerShell

El script de publicación contiene pasos de publicación específicos para la implementación en un sitio web o una máquina virtual. Visual Studio ofrece color de sintaxis para el desarrollo de Windows PowerShell. La Ayuda para las funciones está disponible y puede editar libremente las funciones en el script para satisfacer sus cambiantes requisitos.

### <a name="windows-powershell-module"></a>Módulo de Windows PowerShell

El módulo de Windows PowerShell que Visual Studio genera contiene funciones que el script de publicación usa. Estas son funciones de Azure PowerShell que no están pensadas para modificarse. Consulte [Instalación y configuración de Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Archivo de configuración de JSON

El archivo JSON se crea en la carpeta **Configuraciones** y contiene datos de configuración que especifican exactamente qué recursos se implementarán en Azure. El nombre del archivo que Visual Studio genera es project-name-WAWS-dev.json si ha creado un sitio web o  project name-VM-dev.json, si ha creado una máquina virtual. Este es un ejemplo de un archivo de configuración de JSON que se genera al crear un sitio web. La mayor parte de los valores se explican por sí solos. El nombre del sitio web se genera por Azure, por lo que es posible que no coincida con el nombre del proyecto.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Cuando crea una máquina virtual, el archivo de configuración de JSON es similar al siguiente. Se crea un servicio en la nube como un contenedor para la máquina virtual. La máquina virtual contiene los extremos habituales para el acceso web a través de HTTP y HTTPS, así como extremos para Web Deploy, lo que le permite publicar en el sitio web desde su equipo local, Escritorio remoto y Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Puede editar la configuración de JSON para cambiar lo que ocurre al ejecutar los scripts de publicación. Las secciones `cloudService` y `virtualMachine` son necesarias, pero puede eliminar la sección `databases` si no la necesita. Las propiedades que están vacías en el archivo de configuración predeterminado que Visual Studio genera son opcionales; se requieren las que tienen valores en el archivo de configuración predeterminado.

Si tiene un sitio web que cuenta con varios entornos de implementación (conocidos como ranuras) en lugar de un único sitio de producción en Azure, puede incluir el nombre de la ranura en el nombre del sitio web en el archivo de configuración de JSON. Por ejemplo, si tiene un sitio web llamado **mysite** y una ranura para él llamada **test**, el URI es `mysite-test.cloudapp.net`, pero el nombre correcto que se usará en el archivo de configuración es mysite(test). Solo puede hacerlo si el sitio web y las ranuras ya existen en su suscripción. De no ser así, cree el sitio web ejecutando el script sin especificar la ranura y luego créela en [Azure Portal](https://portal.azure.com/); después ejecute el script con el nombre del sitio web modificado. Para obtener más información sobre las ranuras de implementación para las aplicaciones web, vea [Configuración de entornos de ensayo para aplicaciones web en Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Cómo ejecutar los scripts de publicación

Si nunca ha ejecutado un script de Windows PowerShell antes, debe establecer primero la directiva de ejecución para habilitar la ejecución de los scripts. La directiva es una característica de seguridad para evitar que los usuarios ejecuten scripts de Windows PowerShell si son vulnerables a malware o virus que iconllevan la ejecución de scripts.

### <a name="run-the-script"></a>Ejecute el script

1. Cree el paquete de implementación web para el proyecto. Un paquete de Web Deploy es un archivo comprimido (archivo .zip) que contiene archivos que quiere copiar en el sitio web o máquina virtual. Puede crear paquetes de implementación web en Visual Studio para cualquier aplicación web.

   ![Crear paquete de implementación web](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Para obtener más información, vea [Cómo crear un paquete de implementación web en Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). También puede automatizar la creación de su paquete de Web Deploy, como se describe en [Personalización y ampliación de los scripts de publicación](#customizing-and-extending-the-publish-scripts).

1. En el **Explorador de soluciones**, abra el menú contextual para el script y luego elija **Abrir con PowerShell ISE**.
1. Si ejecuta scripts de Windows PowerShell en este equipo por primera vez, abra una ventana de símbolo del sistema con privilegios de administrador y escriba el siguiente comando:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Inicie sesión en Azure con el siguiente comando.

    ```powershell
    Add-AzureAccount
    ```

    Cuando se le solicite, escriba su nombre de usuario y su contraseña.

    Tenga en cuenta que al automatizar el script, este método de ofrecer credenciales de Azure no funciona. En su lugar, debe usar el archivo `.publishsettings` para ofrecer las credenciales. Una sola vez, use el comando **Get-AzurePublishSettingsFile** para descargar el archivo de Azure y después use **Import-AzurePublishSettingsFile** para importar el archivo. Para obtener instrucciones detalladas, consulte [Instalación y configuración de Azure PowerShell](/powershell/azure/overview).

1. (Opcional) Si quiere crear recursos de Azure como la máquina virtual, la base de datos y el sitio web sin publicar su aplicación web, use el comando **Publish-WebApplication.ps1** con el argumento **-Configuration** establecido en el archivo de configuración de JSON. Esta línea de comandos usa el archivo de configuración de JSON para determinar qué recursos se crearán. Dado que usa la configuración predeterminada para los demás argumentos de línea de comandos, crea los recursos, pero no publica su aplicación web. La opción –Verbose le ofrece más información sobre lo que ocurre.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Use el comando **Publish-WebApplication.ps1** como se muestra en uno de los ejemplos siguientes para invocar al script y publicar su aplicación web. Si necesita invalidar la configuración predeterminada para cualquiera de los demás argumentos, como el nombre de la suscripción, el nombre del paquete de publicación, las credenciales de máquina virtual o las credenciales de servidor de base de datos, puede especificar esos parámetros. Use la opción **–Verbose** opción para ver más información sobre el progreso del proceso de publicación.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Si está creando una máquina virtual, el comando es similar a lo siguiente. En este ejemplo también se muestra cómo especificar las credenciales para varias bases de datos. Para las máquinas virtuales que se estos scripts crean, el certificado de SSL no procede de una entidad de certificación raíz de confianza. Por lo tanto, debe usar la opción **–AllowUntrusted** .

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    El script puede crear bases de datos, pero no crea servidores de bases de datos. Si quiere crear un servidor de base de datos, puede usar la función **New-AzureSqlDatabaseServer** en el módulo de Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Personalización y ampliación de los scripts de publicación

Puede personalizar el script de publicación y el archivo de configuración de JSON. Las funciones del módulo Windows PowerShell **AzureWebAppPublishModule.psm1** no están pensadas para modificarse. Si quiere especificar una base de datos diferente o cambiar algunas de las propiedades de la máquina virtual, edite el archivo de configuración de JSON. Si quiere ampliar la funcionalidad del script para automatizar la creación y las prueba de su proyecto, puede implementar códigos auxiliares de funciones en **Publish-WebApplication.ps1**.

Para automatizar la creación de su proyecto, agregue código que llame a MSBuild en `New-WebDeployPackage` como se muestra en este ejemplo de código. La ruta de acceso al comando MSBuild es diferente en función de la versión de Visual Studio que ha instalado. Para obtener la ruta de acceso correcta, puede usar la función **Get-MSBuildCmd**, como se muestra en este ejemplo.

### <a name="to-automate-building-your-project"></a>Para automatizar la creación del proyecto

1. Agregue el parámetro `$ProjectFile` en la sección de parámetros globales.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copie la función `Get-MSBuildCmd` en el archivo de script.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Reemplace `New-WebDeployPackage` por el código siguiente y reemplace los marcadores de posición en la construcción de la línea `$msbuildCmd`. Este código es para Visual Studio 2019. Si usa Visual Studio 2017, cambie la propiedad **VisualStudioVersion** a `15.0`, "14.0" para Visual Studio 2015 o `12.0` para Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Para compilar la aplicación web, utilice MsBuild.exe. Para obtener ayuda, consulte [referencia de la línea de comandos de MSBuild](../msbuild/msbuild-command-line-reference.md)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=16.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Inicio de la ejecución del comando de compilación

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Llame a la `New-WebDeployPackage` función antes de esta línea: `$Config = Read-ConfigFile $Configuration` para aplicaciones web o `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` para máquinas virtuales.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Invoque el script personalizado desde la línea de comandos con el argumento `$Project`, como se muestra en el ejemplo siguiente:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Para automatizar las pruebas de su aplicación, agregue código a `Test-WebApplication`. Asegúrese de anular los comentarios de las líneas en **Publish-WebApplication.ps1** donde se llama a estas funciones. Si no ofrece una implementación, puede crear su proyecto manualmente con Visual Studio y luego ejecute el script de publicación para publicar en Azure.

## <a name="publishing-function-summary"></a>Publicación del resumen de la función
Para obtener ayuda para las funciones que puede usar en el símbolo del sistema de Windows PowerShell, use el comando `Get-Help function-name`. La ayuda incluye ejemplos y la ayuda de parámetros. El mismo texto de ayuda también se encuentra en los archivos de origen de script, **AzureWebAppPublishModule.psm1** y **Publish-WebApplication.ps1**. El script y la Ayuda se localizan en su idioma de Visual Studio.

**AzureWebAppPublishModule**

| Nombre de la función | Descripción |
| --- | --- |
| Add-AzureSQLDatabase |Crea una nueva base de datos SQL de Azure. |
| Add-AzureSQLDatabases |Crea las bases de datos SQL de Azure a partir de los valores en el archivo de configuración de JSON que Visual Studio genera. |
| Add-AzureVM |Crea una máquina virtual de Azure y devuelve la dirección URL de la máquina virtual implementada. La función configura los requisitos previos y luego llama a la función **New-AzureVM** (módulo de Azure) para crear una nueva máquina virtual. |
| Add-AzureVMEndpoints |Agrega nuevos extremos de entrada a una máquina virtual y devuelve la máquina virtual con el nuevo extremo. |
| Add-AzureVMStorage |Crea una nueva cuenta de Almacenamiento de Azure en la suscripción actual. El nombre de la cuenta comienza con "devtest" seguido de una cadena alfanumérica única. La función devuelve el nombre de la nueva cuenta de almacenamiento. Especifique una ubicación o un grupo de afinidad para la nueva cuenta de almacenamiento. |
| Add-AzureWebsite |Crea un sitio web con el nombre y la ubicación especificados. Esta función llama a la función **New-AzureWebsite** en el módulo de Azure. Si la suscripción no incluye ya un sitio web con el nombre especificado, esta función crea el sitio web y devuelve un objeto de sitio web. De lo contrario, devuelve `$null`. |
| Backup-Subscription |Guarda la suscripción de Azure actual en la variable `$Script:originalSubscription` en el ámbito de script. Esta función guarda la suscripción de Azure actual (como se obtiene mediante `Get-AzureSubscription -Current`) y su cuenta de almacenamiento, y la suscripción que se cambia por este script (almacenada en la variable `$UserSpecifiedSubscription`) y su cuenta de almacenamiento, en el ámbito de script. Al guardar los valores, puede usar una función, como `Restore-Subscription`, para restaurar la suscripción actual original y la cuenta de almacenamiento al estado actual si este estado ha cambiado. |
| Find-AzureVM |Obtiene la máquina virtual de Azure especificada. |
| Format-DevTestMessageWithTime |Antepone la fecha y la hora a un mensaje. Esta función está diseñada para mensajes escritos en las secuencias de Error y Detallado. |
| Get-AzureSQLDatabaseConnectionString |Ensambla una cadena de conexión para conectarse a una base de datos SQL de Azure. |
| Get-AzureVMStorage |Devuelve el nombre de la primera cuenta de almacenamiento con el patrón de nombre "devtest *" (no distingue mayúsculas de minúsculas) en la ubicación especificada o en el grupo de afinidad. Si la cuenta de almacenamiento "devtest*" no coincide con la ubicación o el grupo de afinidad, la función la omite. Especifique una ubicación o un grupo de afinidad. |
| Get-MSDeployCmd |Devuelve un comando para ejecutar la herramienta MsDeploy.exe. |
| New-AzureVMEnvironment |Busca o crea una máquina virtual en la suscripción que coincida con los valores del archivo de configuración de JSON. |
| Publish-WebPackage |Usa MsDeploy.exe y un archivo .zip de paquete de publicación web para implementar recursos en un sitio web. Esta función no genera ninguna salida. Si se produce un error en la llamada a MSDeploy.exe, la función genera una excepción. Para obtener una salida más detallada, use la opción **-Verbose** . |
| Publish-WebPackageToVM |Comprueba los valores de parámetro y luego llama a la función **Publish-WebPackage** . |
| Read-ConfigFile |Valida el archivo de configuración de JSON y devuelve una tabla hash de valores seleccionados. |
| Restore-Subscription |Restablece la suscripción actual a la suscripción original. |
| Test-AzureModule |Devuelve `$true` si la versión del módulo de Azure instalada es 0.7.4 o posterior. Devuelve `$false` si el módulo no está instalado o es de una versión anterior. Esta función no tiene parámetros. |
| Test-AzureModuleVersion |Devuelve `$true` si la versión del módulo de Azure es 0.7.4 o posterior. Devuelve `$false` si el módulo no está instalado o es de una versión anterior. Esta función no tiene parámetros. |
| Test-HttpsUrl |Convierte la URL de entrada en un objeto System.Uri. Devuelve `$True` si la dirección URL es absoluta y su esquema es https. Devuelve `$false` si la dirección URL es relativa, su esquema no es HTTPS o no se puede convertir la cadena de entrada a una dirección URL. |
| Test-Member |Devuelve `$true` si una propiedad o un método es un miembro del objeto. De lo contrario, devuelve `$false`. |
| Write-ErrorWithTime |Escribe un mensaje de error precedido por la hora actual. Esta función llama a la función **Format-DevTestMessageWithTime** para anteponer la hora antes de escribir el mensaje en la secuencia de error. |
| Write-HostWithTime |Escribe un mensaje en el programa host (**Write-Host**) precedido por la hora actual. El efecto de escribir en el programa host varía. La mayoría de los programas que hospedan Windows PowerShell escribe estos mensajes en la salida estándar. |
| Write-VerboseWithTime |Escribe un mensaje detallado precedido por la hora actual. Porque llama a **Write-Verbose**, el mensaje solo aparece cuando el script se ejecuta con el parámetro **Verbose** o cuando la preferencia **VerbosePreference** está establecida en **Continue**. |

**Publish-WebApplication**

| Nombre de la función | Descripción |
| --- | --- |
| New-AzureWebApplicationEnvironment |Crea recursos de Azure, como un sitio web o una máquina virtual. |
| New-WebDeployPackage |Esta función no está implementada. Puede agregar comandos en esta función para generar su proyecto. |
| Publish-AzureWebApplication |Publica una aplicación web en Azure |
| Publish-WebApplication |Crea e implementa Web Apps, máquinas virtuales, instancias de SQL Database y cuentas de almacenamiento para un proyecto web de Visual Studio. |
| Test-WebApplication |Esta función no está implementada. Puede agregar comandos en esta función para probar su aplicación. |

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre el scripting de PowerShell leyendo [Scripting con Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) y consulte otros scripts de Azure PowerShell en el [Centro de scripts](https://azure.microsoft.com/documentation/scripts/).

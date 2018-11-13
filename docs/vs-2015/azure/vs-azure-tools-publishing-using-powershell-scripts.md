---
title: Usar secuencias de comandos de Windows PowerShell para publicar en entornos de desarrollo y pruebas | Microsoft Docs
description: Obtenga información sobre cómo usar scripts de Windows PowerShell desde Visual Studio para publicar en el desarrollo y entornos de prueba.
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002716"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Uso de scripts de Windows PowerShell para publicar en entornos de desarrollo y prueba

Al crear una aplicación web en Visual Studio, puede generar un script de Windows PowerShell que puede utilizar posteriormente para automatizar la publicación de su sitio Web en Azure como una aplicación Web en Azure App Service o una máquina virtual. Puede editar y ampliar el script de Windows PowerShell en el editor de Visual Studio para satisfacer sus requisitos o integrar dicho script con la compilación existente, pruebas y publicar scripts.

Con estas secuencias de comandos, puede aprovisionar versiones personalizadas (también conocido como entornos de desarrollo y pruebas) de su sitio para su uso temporal. Por ejemplo, podría configurar una versión concreta de su sitio Web en una máquina virtual de Azure o en la ranura de ensayo en un sitio Web para ejecutar un conjunto de pruebas, reproducir un error, realizar una corrección de errores, probar un cambio propuesto o configurar un entorno personalizado para una demostración o presentación. Después de crear un script que publique el proyecto, puede volver a crear entornos idénticos volviendo a ejecutar el script según sea necesario, o ejecute el script con su propia versión de la aplicación web para crear un entorno personalizado para las pruebas.

## <a name="prerequisites"></a>Requisitos previos

* Azure SDK 2.3 o posterior. Consulte [descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=624384). (No necesita el SDK de Azure para generar los scripts para proyectos web. Esta característica es para proyectos web, no los roles web en servicios en la nube).
* Azure PowerShell 0.7.4 o posterior. Consulte [cómo instalar y configurar Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) o una versión posterior.

## <a name="additional-tools"></a>Herramientas adicionales

Herramientas y recursos para trabajar con PowerShell en Visual Studio para desarrollo de Azure adicionales están disponibles. Consulte [PowerShell Tools para Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Generar los scripts de publicación

Puede generar los scripts de publicación para una máquina virtual que hospeda el sitio Web cuando se crea un nuevo proyecto siguiendo [estas instrucciones](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). También puede [generar scripts de publicación para aplicaciones web en Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Secuencias de comandos que genera Visual Studio

Visual Studio genera una carpeta de nivel de solución denominada **PublishScripts** que contiene dos archivos de Windows PowerShell, un script de publicación para la máquina virtual o sitio Web y un módulo que contiene funciones que puede usar en el secuencias de comandos. Visual Studio también genera un archivo en el formato JSON que especifica los detalles del proyecto que va a implementar.

### <a name="windows-powershell-publish-script"></a>Script de publicación de Windows PowerShell

El script de publicación contiene pasos de publicación específicos para la implementación en un sitio Web o máquina virtual. Visual Studio ofrece color de sintaxis para el desarrollo de Windows PowerShell. Ayuda para las funciones está disponible, y puede editar libremente las funciones de la secuencia de comandos para satisfacer sus requisitos cambiantes.

### <a name="windows-powershell-module"></a>Módulo de Windows PowerShell

El módulo de Windows PowerShell que Visual Studio genera contiene funciones que utiliza el script de publicación. Estas funciones de Azure PowerShell no pretende ser modificado. Consulte [cómo instalar y configurar Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Archivo de configuración JSON

El archivo JSON se crea en el **configuraciones** carpeta y contiene datos de configuración que especifican exactamente qué recursos se implementarán en Azure. El nombre del archivo que Visual Studio genera es project-nombre-WAWS-dev.json si ha creado un sitio Web o proyecto nombre-VM-dev.json si ha creado una máquina virtual. Este es un ejemplo de un archivo de configuración JSON que se genera cuando se crea un sitio Web. La mayoría de los valores es autoexplicativos. El nombre del sitio Web se genera por Azure, por lo que podría no coincidir con el nombre del proyecto.

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

Cuando se crea una máquina virtual, el archivo de configuración de JSON es similar al siguiente. Se crea un servicio en la nube como un contenedor para la máquina virtual. La máquina virtual contiene los extremos habituales para el acceso web a través de HTTP y HTTPS, así como los puntos de conexión de Web Deploy, que le permite publicar en el sitio Web desde el equipo local, escritorio remoto y Windows PowerShell.

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

Puede editar la configuración de JSON para cambiar lo que sucede al ejecutar los scripts de publicación. El `cloudService` y `virtualMachine` secciones resultan necesarias, pero se puede eliminar el `databases` sección si no lo necesita. Las propiedades que están vacías en el archivo de configuración predeterminado que Visual Studio genera son opcionales; se requieren las propiedades que tienen valores en el archivo de configuración predeterminado.

Si tiene un sitio Web con varios entornos de implementación (conocidos como ranuras) en lugar de un único sitio de producción en Azure, puede incluir el nombre del espacio en el nombre del sitio Web en el archivo de configuración de JSON. Por ejemplo, si tiene un sitio Web que se denomina **mysite** y una ranura para él llamada **probar** , el URI es `mysite-test.cloudapp.net`, pero el nombre correcto que usar en el archivo de configuración es mysite (Test). Solo puede hacerlo si el sitio Web y las ranuras ya existen en su suscripción. Si no existen, cree el sitio Web mediante la ejecución de la secuencia de comandos sin especificar la ranura, a continuación, cree el espacio en el [portal Azure](https://portal.azure.com/), y después ejecute el script con el nombre del sitio Web modificado. Para obtener más información acerca de las ranuras de implementación para las aplicaciones web, consulte [establecer entornos de ensayo para aplicaciones web en Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Cómo ejecutar los scripts de publicación

Si nunca ha ejecutado un script de Windows PowerShell antes, primero debe establecer la directiva de ejecución para habilitar la ejecución de scripts. La directiva es una característica de seguridad para impedir que los usuarios ejecuten scripts de Windows PowerShell si son vulnerables a malware o virus que implican la ejecución de scripts.

### <a name="run-the-script"></a>Ejecute el script

1. Cree el paquete de implementación Web para el proyecto. Un paquete de Web Deploy es un archivo comprimido (archivo .zip) que contienen archivos que se van a copiar en el sitio Web o máquina virtual. Puede crear paquetes de implementación Web en Visual Studio para cualquier aplicación web.

   ![Creación de Web paquete de implementación](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Para obtener más información, consulte [Cómo: crear un paquete de implementación Web en Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). También puede automatizar la creación de su paquete de Web Deploy, como se describe en [personalización y ampliación de los scripts de publicación](#customizing-and-extending-publish-scripts).

1. En **el Explorador de soluciones**, abra el menú contextual de la secuencia de comandos y, a continuación, elija **abrir con PowerShell ISE**.
1. Si ejecuta scripts de Windows PowerShell en este equipo por primera vez, abra una ventana de símbolo del sistema con privilegios de administrador y escriba el siguiente comando:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Inicie sesión en Azure mediante el comando siguiente.

    ```powershell
    Add-AzureAccount
    ```

    Cuando se le solicite, proporcione el nombre de usuario y la contraseña.

    Tenga en cuenta que al automatizar el script, este método de ofrecer credenciales de Azure no funciona. En su lugar, debe usar el `.publishsettings` archivo para proporcionar las credenciales. Una vez, use el comando **Get-AzurePublishSettingsFile** para descargar el archivo de Azure y, posteriormente, use **Import-AzurePublishSettingsFile** para importar el archivo. Para obtener instrucciones detalladas, consulte [cómo instalar y configurar Azure PowerShell](/powershell/azure/overview).

1. (Opcional) Si desea crear recursos de Azure como la máquina virtual, base de datos y el sitio Web sin publicar la aplicación web, utilizan el **Publish-WebApplication.ps1** comando con el **-configuración**argumento establecido en el archivo de configuración de JSON. Esta línea de comandos usa el archivo de configuración JSON para determinar qué recursos se crearán. Dado que usa la configuración predeterminada para el resto de los argumentos de línea de comandos, crea los recursos, pero no publicar la aplicación web. – Verbose opción proporciona más información sobre lo que sucede.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Use la **Publish-WebApplication.ps1** comando tal como se muestra en uno de los ejemplos siguientes para invocar el script y publicar la aplicación web. Si necesita invalidar la configuración predeterminada para cualquiera de los demás argumentos, como el nombre de la suscripción, el nombre del paquete, las credenciales de la máquina virtual o las credenciales del servidor de base de datos de publicación, puede especificar esos parámetros. Use la **– Verbose** opción para obtener más información sobre el progreso del proceso de publicación.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Si está creando una máquina virtual, el comando es similar al siguiente. Este ejemplo también muestra cómo especificar las credenciales para varias bases de datos. Para las máquinas virtuales que crean estas secuencias de comandos, el certificado SSL no es de una entidad emisora raíz de confianza. Por lo tanto, deberá usar el **– AllowUntrusted** opción.

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

    El script puede crear bases de datos, pero no crea servidores de base de datos. Si desea crear un servidor de base de datos, puede usar el **New-AzureSqlDatabaseServer** función del módulo de Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Personalizar y ampliar los scripts de publicación

Puede personalizar el script de publicación y el archivo de configuración JSON. Las funciones del módulo de Windows PowerShell **AzureWebAppPublishModule.psm1** no están pensadas para modificarse. Si solo desea especificar una base de datos diferente o cambiar algunas de las propiedades de la máquina virtual, edite el archivo de configuración de JSON. Si desea ampliar la funcionalidad de la secuencia de comandos para automatizar la creación y prueba del proyecto, puede implementar códigos auxiliares de función en **Publish-WebApplication.ps1**.

Para automatizar la creación del proyecto, agregue el código que llame a MSBuild en `New-WebDeployPackage` tal como se muestra en este ejemplo de código. La ruta de acceso al comando MSBuild es diferente según la versión de Visual Studio que haya instalado. Para obtener la ruta de acceso correcta, puede usar la función **Get-MSBuildCmd**, tal y como se muestra en este ejemplo.

### <a name="to-automate-building-your-project"></a>Para automatizar la creación del proyecto

1. Agregar el `$ProjectFile` parámetro en la sección de parámetros globales.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copie la función `Get-MSBuildCmd` al archivo de script.

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

1. Reemplace `New-WebDeployPackage` con el código siguiente y reemplace los marcadores de posición en la construcción de la línea `$msbuildCmd`. Este código es para Visual Studio 2015. Si usa Visual Studio 2017, cambie el **VisualStudioVersion** propiedad `15.0` (`12.0` para Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Para compilar la aplicación web, utilice MsBuild.exe. Para obtener ayuda, consulte la referencia de línea de comandos de MSBuild en: [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Iniciar la ejecución del comando de compilación

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

1. Llame a la `New-WebDeployPackage` función antes de esta línea: `$Config = Read-ConfigFile $Configuration` para las aplicaciones web o `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` para las máquinas virtuales.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Invoque el script personalizado desde la línea de comandos con el `$Project` argumento, como en el ejemplo siguiente:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Para automatizar las pruebas de la aplicación, agregue código al `Test-WebApplication`. Asegúrese de comentarios de las líneas en **Publish-WebApplication.ps1** donde se llama a estas funciones. Si no proporciona una implementación, puede compilar manualmente el proyecto con Visual Studio y, a continuación, ejecute el script de publicación para publicar en Azure.

## <a name="publishing-function-summary"></a>Resumen de la función de publicación
Para obtener ayuda sobre funciones que puede usar en el símbolo del sistema de Windows PowerShell, use el comando `Get-Help function-name`. La Ayuda incluye la Ayuda de parámetros y ejemplos. También es el mismo texto de ayuda en los archivos de origen de la secuencia de comandos **AzureWebAppPublishModule.psm1** y **Publish-WebApplication.ps1**. La secuencia de comandos y la Ayuda se localizan en su idioma de Visual Studio.

**AzureWebAppPublishModule**

| Nombre de la función | Descripción |
| --- | --- |
| Agregar-AzureSQLDatabase |Crea una nueva base de datos de SQL Azure. |
| Add-AzureSQLDatabases |Crea las bases de datos SQL de Azure a partir de los valores en el archivo de configuración JSON que genera Visual Studio. |
| Add-AzureVM |Crea una máquina virtual de Azure y devuelve la dirección URL de la máquina virtual implementada. La función configura los requisitos previos y, a continuación, llama a la **New-AzureVM** función (módulo de Azure) para crear una nueva máquina virtual. |
| Add-AzureVMEndpoints |Agrega nuevos extremos de entrada a una máquina virtual y devuelve la máquina virtual con el nuevo punto de conexión. |
| Add-AzureVMStorage |Crea una nueva cuenta de almacenamiento de Azure en la suscripción actual. El nombre de la cuenta comienza con "devtest" seguido de una cadena alfanumérica única. La función devuelve el nombre de la nueva cuenta de almacenamiento. Especifique una ubicación o un grupo de afinidad para la nueva cuenta de almacenamiento. |
| Add-AzureWebsite |Crea un sitio Web con el nombre especificado y la ubicación. Esta función llama a la **New-AzureWebsite** función del módulo de Azure. Si la suscripción ya no incluye un sitio Web con el nombre especificado, esta función crea el sitio Web y devuelve un objeto de sitio Web. De lo contrario, devuelve `$null`. |
| Suscripción de copia de seguridad |Guarda la suscripción de Azure actual en el `$Script:originalSubscription` variable en el ámbito del script. Esta función guarda la suscripción de Azure actual (obtenida por `Get-AzureSubscription -Current`) y su cuenta de almacenamiento y la suscripción que se cambia por este script (almacenada en la variable `$UserSpecifiedSubscription`) y su cuenta de almacenamiento, en el ámbito del script. Al guardar estos valores, puede usar una función, como `Restore-Subscription`, para restaurar la cuenta de almacenamiento y la suscripción actual original al estado actual, si ha cambiado el estado actual. |
| Find-AzureVM |Obtiene la máquina virtual de Azure especificada. |
| Format-DevTestMessageWithTime |Antepone la fecha y hora a un mensaje. Esta función está diseñada para mensajes escritos en los flujos de Error y detallado. |
| Get-AzureSQLDatabaseConnectionString |Ensambla una cadena de conexión para conectarse a una base de datos SQL de Azure. |
| Get-AzureVMStorage |Devuelve el nombre de la primera cuenta de almacenamiento con el patrón de nombre "devtest *" (mayúsculas de minúsculas) en la ubicación especificada o el grupo de afinidad. Si el "devtest*" cuenta de almacenamiento no coincide con la ubicación o el grupo de afinidad, la función la omite. Especifique una ubicación o un grupo de afinidad. |
| Get-MSDeployCmd |Devuelve un comando para ejecutar la herramienta MsDeploy.exe. |
| New-AzureVMEnvironment |Busca o crea una máquina virtual en la suscripción que coincide con los valores en el archivo de configuración de JSON. |
| Publish-WebPackage |Utiliza MsDeploy.exe y un sitio web publican el paquete. Archivo ZIP para implementar recursos en un sitio Web. Esta función no genera ningún resultado. Si se produce un error en la llamada a MSDeploy.exe, la función produce una excepción. Para obtener un resultado más detallado, utilice el **-Verbose** opción. |
| Publish-WebPackageToVM |Comprueba los valores de parámetro y, a continuación, llama a la **Publish-WebPackage** función. |
| Read-ConfigFile |Valida el archivo de configuración JSON y devuelve una tabla hash de valores seleccionados. |
| Suscripción de restauración |Restablece la suscripción actual a la suscripción original. |
| Test-AzureModule |Devuelve `$true` si la versión del módulo de Azure instalado es 0.7.4 o posterior. Devuelve `$false` si el módulo no está instalado o es una versión anterior. Esta función no tiene parámetros. |
| Prueba AzureModuleVersion |Devuelve `$true` si la versión del módulo de Azure es 0.7.4 o posterior. Devuelve `$false` si el módulo no está instalado o es una versión anterior. Esta función no tiene parámetros. |
| Prueba HttpsUrl |Convierte la URL de entrada en un objeto System.Uri. Devuelve `$True` si la dirección URL es absoluta y su esquema es https. Devuelve `$false` si la dirección URL es relativa, su esquema no es HTTPS o no se puede convertir la cadena de entrada a una dirección URL. |
| Miembro de la prueba |Devuelve `$true` si una propiedad o método es un miembro del objeto. De lo contrario, devuelve `$false`. |
| Escritura ErrorWithTime |Escribe un mensaje de error precedido por la hora actual. Esta función llama a la **Format-DevTestMessageWithTime** para anteponer la hora antes de escribir el mensaje en la secuencia de Error. |
| Escritura HostWithTime |Escribe un mensaje en el programa host (**Write-Host**) prefijado con la hora actual. El efecto de escribir en el programa host varía. Mayoría de los programas que hospedan Windows PowerShell escribe estos mensajes en la salida estándar. |
| Escritura VerboseWithTime |Escribe un mensaje detallado precedido por la hora actual. Porque llama a **Write-Verbose**, aparece el mensaje sólo cuando se ejecuta el script con el **detallado** parámetro o cuando el **VerbosePreference** está establecida en  **Continuar**. |

**WebApplication publicar**

| Nombre de la función | Descripción |
| --- | --- |
| Nuevo AzureWebApplicationEnvironment |Crea recursos de Azure, como un sitio Web o máquina virtual. |
| Nuevo WebDeployPackage |Esta función no está implementada. Puede agregar comandos en esta función para compilar el proyecto. |
| AzureWebApplication publicar |Publica una aplicación web en Azure. |
| WebApplication publicar |Crea e implementa aplicaciones Web, máquinas virtuales, bases de datos SQL y las cuentas de almacenamiento para un proyecto web de Visual Studio. |
| WebApplication de prueba |Esta función no está implementada. Puede agregar comandos en esta función para probar la aplicación. |

## <a name="next-steps"></a>Pasos siguientes
Más información sobre scripting de PowerShell leyendo [Scripting con Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) y vea otros scripts de PowerShell de Azure en el [Script Center](https://azure.microsoft.com/documentation/scripts/).

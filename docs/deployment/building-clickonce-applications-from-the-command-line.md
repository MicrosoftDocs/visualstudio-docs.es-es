---
title: Compilar aplicaciones ClickOnce desde la línea de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8ce0753c63f1dcc177f36149cad9789ec150ab
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787679"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Compilación de aplicaciones ClickOnce desde la línea de comandos
En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], puede compilar proyectos desde la línea de comandos, incluso si se crean en el entorno de desarrollo integrado (IDE) de. De hecho, puede volver a generar un proyecto creado [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] con en otro equipo que tenga solo el .NET Framework instalado. Esto le permite reproducir una compilación mediante un proceso automatizado, por ejemplo, en un laboratorio de compilación central o mediante técnicas de scripting avanzadas más allá del ámbito de la creación del proyecto.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Usar MSBuild para reproducir implementaciones de aplicaciones ClickOnce
 Al invocar MSBuild/target: Publish en la línea de comandos, indica al sistema MSBuild que compile el proyecto y cree una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en la carpeta Publish. Esto es equivalente a seleccionar el comando **publicar** en el IDE.

 Este comando ejecuta *MSBuild. exe*, que se encuentra en la ruta de acceso del entorno del símbolo del sistema de Visual Studio.

 Un "destino" es un indicador de MSBuild sobre cómo procesar el comando. Los destinos clave son el destino "Build" y el destino "Publish". El destino de compilación es el equivalente a seleccionar el comando de compilación (o presionar F5) en el IDE. Si solo desea compilar el proyecto, puede hacerlo escribiendo `msbuild`. Este comando funciona porque el destino de compilación es el destino predeterminado para todos los proyectos [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]generados por. Esto significa que no es necesario especificar explícitamente el destino de compilación. Por lo tanto `msbuild` , escribir es la misma operación `msbuild /target:build`que escribir.

 El `/target:publish` comando indica a MSBuild que invoque el destino de publicación. El destino de publicación depende del destino de compilación. Esto significa que la operación de publicación es un superconjunto de la operación de compilación. Por ejemplo, si realizó un cambio en uno de los archivos de Visual Basic C# o de código fuente, la operación de publicación volvería a generar automáticamente el ensamblado correspondiente.

 Para obtener información sobre cómo generar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] una implementación completa mediante la herramienta de línea de comandos Mage. exe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para crear el [manifiesto, vea Tutorial: Implementar manualmente una aplicación](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)ClickOnce.

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Crear y compilar una aplicación ClickOnce básica con MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Para crear y publicar un proyecto ClickOnce

1. Abra Visual Studio y cree un nuevo proyecto.

    Elija la plantilla de proyecto **aplicación de escritorio de Windows** y `CmdLineDemo`asigne al proyecto el nombre.

1. En el menú compilar, haga clic en el comando **publicar** .

    Este paso garantiza que el proyecto esté configurado correctamente para generar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de aplicación.

    Aparece el Asistente para publicación.

1. En el Asistente para publicación, haga clic en **Finalizar**.

    Visual Studio genera y muestra la página web predeterminada, denominada *Publish. htm*.

1. Guarde el proyecto y tome nota de la ubicación de la carpeta en la que se almacena.

   En los pasos anteriores se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un proyecto que se ha publicado por primera vez. Ahora puede reproducir la compilación fuera del IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Para reproducir la compilación desde la línea de comandos

1. Salga de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. En el menú **Inicio** de Windows, haga clic en **todos los programas**, **Microsoft Visual Studio**, **Visual Studio Tools**y, a continuación, en **símbolo del sistema de Visual Studio**. Debe abrir un símbolo del sistema en la carpeta raíz del usuario actual.

3. En el **símbolo del sistema de Visual Studio**, cambie el directorio actual a la ubicación del proyecto que acaba de crear. Por ejemplo, escriba `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Para quitar los archivos existentes generados en "para crear y publicar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un proyecto", `rmdir /s publish`escriba.

    Este paso es opcional, pero se asegura de que todos los archivos nuevos fueron generados por la compilación de línea de comandos.

5. Escriba `msbuild /target:publish`.

   En los pasos anteriores se generará [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] una implementación de aplicación completa en una subcarpeta del proyecto denominada **Publish**. *CmdLineDemo. Application* es el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. La carpeta *cmdlinedemo_ 1.0.0.0* contiene los archivos *CmdLineDemo. exe* y *CmdLineDemo. exe. manifest*, el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. *Setup. exe* es el programa previo, que está configurado de forma predeterminada para instalar el .NET Framework. La carpeta DotNetFX contiene los redistribuibles para el .NET Framework. Este es el conjunto completo de archivos que necesita para implementar la aplicación a través de Internet o mediante UNC o CD/DVD.
   
> [!NOTE]
> El sistema MSBuild usa la opción **PublishDir** para especificar la ubicación de salida, por ejemplo `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Publicación de propiedades
 Al publicar la aplicación en los procedimientos anteriores, el Asistente para publicación inserta las siguientes propiedades en el archivo del proyecto. Estas propiedades influyen directamente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en cómo se produce la aplicación.

 En *CmdLineDemo. vbproj* / *CmdLineDemo. csproj*:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 Puede invalidar cualquiera de estas propiedades en la línea de comandos sin modificar el propio archivo de proyecto. Por ejemplo, lo siguiente generará la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de la aplicación sin el programa previo:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Las propiedades de publicación se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] controlan en desde las páginas de propiedades **publicar**, **seguridad**y **firma** del **Diseñador de proyectos**. A continuación se muestra una descripción de las propiedades de publicación, junto con una indicación de cómo se establece cada una en las distintas páginas de propiedades del diseñador de aplicaciones:

- `AssemblyOriginatorKeyFile`determina el archivo de clave que se usa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para firmar los manifiestos de aplicación. Esta misma clave también se puede usar para asignar un nombre seguro a los ensamblados. Esta propiedad se establece en la página **firma** del **Diseñador de proyectos**.

  Las siguientes propiedades se establecen en la página **seguridad** :

- **Habilitar la configuración de seguridad** de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ClickOnce determina si se generan manifiestos. Cuando se crea un proyecto por primera [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vez, la generación de manifiestos está desactivada de forma predeterminada. El asistente activará automáticamente esta marca al publicar por primera vez.

- **TargetZone** determina el nivel de confianza que se va a emitir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en el manifiesto de aplicación. Los valores posibles son "Internet", "LocalIntranet" y "Custom". Internet y LocalIntranet harán que se emita un conjunto de permisos predeterminado en el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. LocalIntranet es el valor predeterminado y básicamente significa plena confianza. Personalizado especifica que solo los permisos especificados explícitamente en el archivo *. manifest* de la aplicación base se emitirán en el manifiesto de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. El archivo *app. manifest* es un archivo de manifiesto parcial que contiene solo las definiciones de información de confianza. Es un archivo oculto que se agrega automáticamente al proyecto cuando se configuran los permisos en la página **seguridad** .

  Las siguientes propiedades se establecen en la página **publicar** :

- `PublishUrl`es la ubicación donde se publicará la aplicación en el IDE. Se inserta en el manifiesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de aplicación si no se `InstallUrl` especifica `UpdateUrl` la propiedad o.

- `ApplicationVersion`Especifica la versión de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Se trata de un número de versión de cuatro dígitos. Si el último dígito es un "*", `ApplicationRevision` se sustituye por el valor insertado en el manifiesto en tiempo de compilación.

- `ApplicationRevision`Especifica la revisión. Es un entero que se incrementa cada vez que se publica en el IDE. Tenga en cuenta que no se incrementa automáticamente para las compilaciones realizadas en la línea de comandos.

- `Install`determina si la aplicación es una aplicación instalada o una aplicación de ejecución desde la Web.

- `InstallUrl`(no se muestra) es la ubicación desde la que los usuarios van a instalar la aplicación. Si se especifica, este valor se graba en el programa previo *setup. exe* si la `IsWebBootstrapper` propiedad está habilitada. También se inserta en el manifiesto de aplicación si `UpdateUrl` no se especifica.

- `SupportUrl`(no se muestra) es la ubicación vinculada en el cuadro de diálogo **Agregar o quitar programas** de una aplicación instalada.

  Las siguientes propiedades se establecen en el cuadro de diálogo actualizaciones de la **aplicación** , al que se obtiene acceso desde la página **publicar** .

- `UpdateEnabled`indica si la aplicación debe comprobar si hay actualizaciones.

- `UpdateMode`especifica actualizaciones en primer plano o en segundo plano.

- `UpdateInterval`Especifica la frecuencia con la que la aplicación debe comprobar si hay actualizaciones.

- `UpdateIntervalUnits`Especifica si el `UpdateInterval` valor se encuentra en unidades de horas, días o semanas.

- `UpdateUrl`(no se muestra) es la ubicación desde la que la aplicación recibirá actualizaciones. Si se especifica, este valor se inserta en el manifiesto de aplicación.

- Las siguientes propiedades se establecen en el cuadro de diálogo **Opciones de publicación** , al que se obtiene acceso desde la página **publicar** .

- `PublisherName`especifica el nombre del publicador que se muestra en el mensaje que se muestra al instalar o ejecutar la aplicación. En el caso de una aplicación instalada, también se utiliza para especificar el nombre de la carpeta en el menú **Inicio** .

- `ProductName`especifica el nombre del producto que se muestra en el mensaje que se muestra al instalar o ejecutar la aplicación. En el caso de una aplicación instalada, también se usa para especificar el nombre de acceso directo en el menú **Inicio** .

- Las siguientes propiedades se establecen en el cuadro de diálogo **requisitos previos** , al que se obtiene acceso desde la página **publicar** .

- `BootstrapperEnabled`determina si se debe generar el programa previo *setup. exe* .

- `IsWebBootstrapper`determina si el programa previo *setup. exe* funciona a través de web o en modo basado en disco.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL y UpdateURL
 En la tabla siguiente se muestran las cuatro opciones de dirección URL para la implementación ClickOnce.

|Opción de dirección URL|DESCRIPCIÓN|
|----------------|-----------------|
|`PublishURL`|Es obligatorio si va a publicar la aplicación ClickOnce en un sitio Web.|
|`InstallURL`|Opcional. Establezca esta opción de dirección URL si el sitio de instalación es `PublishURL`diferente del. Por ejemplo, puede establecer `PublishURL` en una ruta de acceso FTP y establecer el `InstallURL` en una dirección URL Web.|
|`SupportURL`|Opcional. Establezca esta opción de dirección URL si el sitio de soporte técnico `PublishURL`es diferente del. Por ejemplo, puede establecer el `SupportURL` en el sitio web de soporte al cliente de su compañía.|
|`UpdateURL`|Opcional. Establezca esta opción de dirección URL si la ubicación de actualización es `InstallURL`diferente de. Por ejemplo, puede establecer `PublishURL` en una ruta de acceso FTP y establecer el `UpdateURL` en una dirección URL Web.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Tutorial: Implementación manual de una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

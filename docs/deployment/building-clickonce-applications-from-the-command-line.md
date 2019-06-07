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
ms.openlocfilehash: fc3cdf49746340c76855e9afb000c754464d6223
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746085"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Compilación de aplicaciones ClickOnce desde la línea de comandos
En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], puede compilar proyectos desde la línea de comandos, incluso si se crean en el entorno de desarrollo integrado (IDE). De hecho, puede volver a generar un proyecto creado con [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] en otro equipo que tenga solo instalado .NET Framework. Esto le permite reproducir una compilación mediante un proceso automatizado, por ejemplo, en una compilación central laboratorio o uso de técnicas avanzadas de scripting fuera del ámbito de compilar el proyecto en Sí.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Usar MSBuild para reproducir las implementaciones de aplicaciones ClickOnce
 Al invocar msbuild/target: Publish en la línea de comandos, se indica al sistema de MSBuild para compilar el proyecto y crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en la carpeta de publicación. Esto equivale a seleccionar la **publicar** comando en el IDE.

 Este comando ejecuta *msbuild.exe*, que se encuentra en la ruta de acceso en el entorno de línea de comandos de Visual Studio.

 Un "destino" es un indicador para MSBuild acerca de cómo procesar el comando. Los destinos clave son el destino "build" y el destino de "publicar". El destino de compilación es el equivalente a seleccionar la compilación de comando (o presionando F5) en el IDE. Si solo desea compilar el proyecto, puede hacerlo escribiendo `msbuild`. Este comando funciona porque el destino de compilación es el destino predeterminado para todos los proyectos generados por [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Esto significa que no es necesario explícitamente especificar el destino de compilación. Por lo tanto, escribir `msbuild` es la misma operación que escribir `msbuild /target:build`.

 El `/target:publish` comando indica a MSBuild para invocar el destino de publicación. El destino de publicación depende del destino de compilación. Esto significa que la operación de publicación es un supraconjunto de la operación de compilación. Por ejemplo, si ha realizado un cambio en uno de los archivos de código fuente de Visual Basic o C#, el ensamblado correspondiente podría generarse automáticamente por la operación de publicación.

 Para obtener información sobre la generación de un completo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación utilizando la herramienta de línea de comandos Mage.exe para crear su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto, vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Crear y compilar una aplicación ClickOnce básica con MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Para crear y publicar un proyecto de ClickOnce

1. Abra Visual Studio y cree un nuevo proyecto.

    Elija la **aplicación de escritorio de Windows** plantilla de proyecto y denomine al proyecto `CmdLineDemo`.

1. Desde el **compilar** menú, haga clic en el **publicar** comando.

    Este paso garantiza que el proyecto está configurado correctamente para generar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de la aplicación.

    Aparece el Asistente para publicación.

1. En el Asistente para publicación, haga clic en **finalizar**.

    Visual Studio genera y muestra la página Web predeterminada, denominada *Publish.htm*.

1. Guarde el proyecto y anote la ubicación de la carpeta donde se almacena.

   Los pasos anteriores crean un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proyecto que se publicó por primera vez. Ahora puede reproducir la compilación fuera del IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Para reproducir la compilación desde la línea de comandos

1. Salga de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Desde el Windows **iniciar** menú, haga clic en **todos los programas**, a continuación, **Microsoft Visual Studio**, a continuación, **Visual Studio Tools**, entonces **Símbolo del sistema de visual Studio**. Esto debería abrir un símbolo del sistema en la carpeta raíz del usuario actual.

3. En el **Visual Studio Command Prompt**, cambie el directorio actual a la ubicación del proyecto compiló anteriormente. Por ejemplo, escriba `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Para quitar los archivos existentes generados en "para crear y publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proyecto," tipo `rmdir /s publish`.

    Este paso es opcional, pero garantiza que todos los nuevos archivos fueron creados por la compilación de línea de comandos.

5. Escriba `msbuild /target:publish`.

   Los pasos anteriores producirán un completo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de aplicaciones en una subcarpeta del proyecto denominada **publicar**. *CmdLineDemo.application* es el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. La carpeta *CmdLineDemo_1.0.0.0* contiene los archivos *CmdLineDemo.exe* y *CmdLineDemo.exe.manifest*, el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. *Setup.exe* es el programa previo, que está configurado para instalar .NET Framework de forma predeterminada. La carpeta DotNetFX contiene los archivos redistribuibles de .NET Framework. Esto es todo el conjunto de archivos que necesita para implementar la aplicación a través de Internet o a través de UNC o CD/DVD.

## <a name="publish-properties"></a>Publicación de propiedades
 Cuando se publica la aplicación en los procedimientos anteriores, las siguientes propiedades se insertan en el archivo de proyecto mediante el Asistente para publicación. Estas propiedades influyen directamente en el modo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se genera la aplicación.

 En *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*:

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

 Puede invalidar cualquiera de estas propiedades en la línea de comandos sin modificar el archivo del proyecto. Por ejemplo, la siguiente generará el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de la aplicación sin el programa previo:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Propiedades de publicación se controlan en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde el **publicar**, **seguridad**, y **firma** páginas de propiedades de la **Diseñador de proyectos** . A continuación encontrará una descripción de las propiedades de publicación, junto con una indicación de cómo cada uno se establece en varias páginas de propiedades del Diseñador de aplicación:

- `AssemblyOriginatorKeyFile` Determina el archivo de clave utilizado para firmar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos de aplicación. También se puede usar esta misma clave para asignar un nombre seguro a los ensamblados. Esta propiedad se establece en el **firma** página de la **Diseñador de proyectos**.

  Las siguientes propiedades se establecen en el **seguridad** página:

- **Habilitar la configuración de seguridad de ClickOnce** determina si [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se generan los manifiestos. Cuando un proyecto se crea inicialmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la generación de manifiestos está desactivada de forma predeterminada. El asistente, activará automáticamente esta marca cuando publique por primera vez.

- **TargetZone** determina el nivel de confianza que se emitirá en su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Los valores posibles son "Internet", "LocalIntranet" y "Custom". Internet e intranet local provocará un conjunto de permisos predeterminado que se emitirá en su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Intranet local es el valor predeterminado y básicamente significa plena confianza. Custom indica que solo los permisos que se especifica explícitamente en la base de *app.manifest* son archivos que se emitirá en el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. El *app.manifest* archivo es un archivo de manifiesto parcial que contiene solo las definiciones de la información de confianza. Es un archivo oculto, se agrega automáticamente al proyecto cuando se configuren permisos en el **seguridad** página.

  Las siguientes propiedades se establecen en el **publicar** página:

- `PublishUrl` es la ubicación donde se publicará la aplicación en el IDE. Éste se inserta en la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación si no la `InstallUrl` o `UpdateUrl` se especifica la propiedad.

- `ApplicationVersion` Especifica la versión de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Se trata de un número de versión de cuatro dígitos. Si el último dígito es un "*", el `ApplicationRevision` se sustituye por el valor insertado en el manifiesto en tiempo de compilación.

- `ApplicationRevision` Especifica la revisión. Esto es un entero que se incrementa cada vez que publique en el IDE. Tenga en cuenta que no se incrementa automáticamente para las compilaciones realizadas desde la línea de comandos.

- `Install` Determina si la aplicación es una aplicación instalada o una aplicación en ejecución desde el Web.

- `InstallUrl` (no mostrado) es la ubicación donde los usuarios instalarán la aplicación. Si se especifica, este valor se graba en el *setup.exe* arranque si la `IsWebBootstrapper` propiedad está habilitada. También se inserta en la if de manifiesto de aplicación el `UpdateUrl` no se especifica.

- `SupportUrl` la ubicación (no mostrado) está vinculada en el **agregar o quitar programas** cuadro de diálogo para una aplicación instalada.

  Las siguientes propiedades se establecen el **actualizaciones de la aplicación** cuadro de diálogo, tiene acceso desde el **publicar** página.

- `UpdateEnabled` indica si la aplicación debe buscar actualizaciones.

- `UpdateMode` Especifica las actualizaciones de primer plano o actualizaciones en segundo plano.

- `UpdateInterval` Especifica con qué frecuencia debe buscar actualizaciones la aplicación.

- `UpdateIntervalUnits` Especifica si el `UpdateInterval` valor está en unidades de horas, días o semanas.

- `UpdateUrl` (no mostrado) es la ubicación desde la que recibirá las actualizaciones de la aplicación. Si se especifica, este valor se inserta en el manifiesto de aplicación.

- Las siguientes propiedades se establecen el **opciones de publicación** cuadro de diálogo, tiene acceso desde el **publicar** página.

- `PublisherName` Especifica el nombre del publicador que se muestra en el símbolo del sistema que se muestra al instalar o ejecutar la aplicación. En el caso de una aplicación instalada, también se usa para especificar el nombre de carpeta en el **iniciar** menú.

- `ProductName` Especifica el nombre del producto que se muestra en el símbolo del sistema que se muestra al instalar o ejecutar la aplicación. En el caso de una aplicación instalada, también se usa para especificar el nombre de método abreviado en el **iniciar** menú.

- Las siguientes propiedades se establecen el **requisitos previos** cuadro de diálogo, tiene acceso desde el **publicar** página.

- `BootstrapperEnabled` Determina si se debe generar el *setup.exe* programa previo.

- `IsWebBootstrapper` Determina si el *setup.exe* programa previo funciona a través de Internet o en modo basado en disco.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL y UpdateURL
 En la tabla siguiente se muestra las cuatro opciones de dirección URL para la implementación de ClickOnce.

|Opción de dirección URL|Descripción|
|----------------|-----------------|
|`PublishURL`|Necesario si va a publicar la aplicación ClickOnce para un sitio Web.|
|`InstallURL`|Opcional. Establezca esta opción de dirección URL si la instalación de sitio es diferente de la `PublishURL`. Por ejemplo, puede establecer el `PublishURL` a una ruta de acceso FTP y un conjunto el `InstallURL` a una dirección URL de Web.|
|`SupportURL`|Opcional. Establezca esta opción de dirección URL si el sitio de soporte técnico es diferente de la `PublishURL`. Por ejemplo, puede establecer el `SupportURL` al sitio de Web de atención al cliente de su empresa.|
|`UpdateURL`|Opcional. Establezca esta opción de dirección URL si la ubicación de actualización es distinta a la `InstallURL`. Por ejemplo, puede establecer el `PublishURL` a una ruta de acceso FTP y un conjunto el `UpdateURL` a una dirección URL de Web.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
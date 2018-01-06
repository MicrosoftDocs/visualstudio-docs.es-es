---
title: "Compilar aplicaciones ClickOnce desde la línea de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 39a64737c3e34b7e0c4d89824b22f169d60d4fd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Compilar aplicaciones ClickOnce desde la línea de comandos
En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], puede generar proyectos desde la línea de comandos, incluso si se crean en el entorno de desarrollo integrado (IDE). De hecho, puede volver a generar un proyecto creado con [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] en otro equipo que tiene sólo el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] instalado. Esto le permite reproducir una compilación mediante un proceso automatizado, por ejemplo, en una compilación central laboratorio o mediante técnicas avanzadas de scripting fuera del ámbito de compilar el proyecto en Sí.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Usar MSBuild para reproducir las implementaciones de aplicaciones ClickOnce  
 Al invocar msbuild/target: Publish en la línea de comandos, se indica al sistema de MSBuild para compilar el proyecto y crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en la carpeta de publicación. Esto es equivalente a seleccionar el **publicar** comando en el IDE.  
  
 Este comando ejecuta msbuild.exe, que se encuentra en la ruta de acceso en el entorno de línea de comandos de Visual Studio.  
  
 Un "destino" es un indicador para MSBuild acerca de cómo procesar el comando. Los destinos clave son el destino "build" y el destino "publicar". El destino de compilación es el equivalente a seleccionar la compilación comando (o presionar F5) en el IDE. Si sólo desea compilar el proyecto, puede lograr que escribiendo `msbuild`. Este comando funciona porque el destino build es el destino predeterminado para todos los proyectos generados por [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Esto significa que no es necesario explícitamente especificar el destino build. Por lo tanto, escriba `msbuild` es la misma operación que escribir `msbuild /target:build`.  
  
 El `/target:publish` comando indica a MSBuild que invoque el destino de publicación. El destino de publicación depende del destino de compilación. Esto significa que la operación de publicación es un supraconjunto de la operación de compilación. Por ejemplo, si ha realizado un cambio en uno de los archivos de código fuente de Visual Basic o C#, automáticamente se regenerará el ensamblado correspondiente mediante la operación de publicación.  
  
 Para obtener información acerca de cómo generar un completo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación utilizando la herramienta de línea de comandos Mage.exe para crear su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto, consulte [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Crear y compilar una aplicación ClickOnce de Basic con MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Para crear y publicar un proyecto de ClickOnce  
  
1.  Haga clic en **nuevo proyecto** desde el **archivo** menú. Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  Seleccione **aplicación de Windows** y asígnele el nombre `CmdLineDemo`.  
  
3.  Desde el **generar** menú, haga clic en el **publicar** comando.  
  
     Este paso garantiza que el proyecto está correctamente configurado para generar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de aplicaciones.  
  
     Aparece el Asistente para publicación.  
  
4.  En el Asistente para publicación, haga clic en **finalizar**.  
  
     Visual Studio genera y muestra la página Web predeterminada, denominada Publish.htm.  
  
5.  Guarde el proyecto y tome nota de la ubicación de la carpeta en la que se almacena.  
  
 Los pasos anteriores para crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proyecto que se ha publicado por primera vez. Ahora puede reproducir la generación fuera del IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Para reproducir la compilación desde la línea de comandos  
  
1.  Salga de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Desde las ventanas **iniciar** menú, haga clic en **todos los programas**, a continuación, **Microsoft Visual Studio**, a continuación, **Visual Studio Tools**, a continuación, **Símbolo del sistema de visual Studio**. Se debería abrir un símbolo del sistema en la carpeta raíz del usuario actual.  
  
3.  En el **Visual Studio Command Prompt**, cambie el directorio actual a la ubicación del proyecto que generó anteriormente. Por ejemplo, escriba `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Para quitar los archivos existentes generados en "para crear y publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proyecto," tipo `rmdir /s publish`.  
  
     Este paso es opcional, pero garantiza que todos los nuevos archivos fueron creados por la compilación de línea de comandos.  
  
5.  Escriba `msbuild /target:publish`.  
  
 Los pasos anteriores producirán un completo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de aplicación en una subcarpeta del proyecto denominada P**publicar**. CmdLineDemo.application es el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. La carpeta CmdLineDemo_1.0.0.0 contiene los archivos CmdLineDemo.exe y CmdLineDemo.exe.manifest, el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Setup.exe es el programa previo, que de forma predeterminada está configurado para instalar el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. La carpeta DotNetFX contiene los archivos redistribuibles para la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Esto es todo el conjunto de archivos que necesita para implementar la aplicación a través de Internet o a través de UNC o CD/DVD.  
  
## <a name="publishing-properties"></a>Propiedades de publicación  
 Cuando se publica la aplicación en los procedimientos anteriores, las propiedades siguientes se insertan en el archivo de proyecto mediante el Asistente para publicación. Estas propiedades influyen directamente en el modo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se genera la aplicación.  
  
 En CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
```  
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
  
 Puede invalidar cualquiera de estas propiedades en la línea de comandos sin modificar el propio archivo de proyecto. Por ejemplo, la siguiente generará el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación de aplicación sin el programa previo:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Propiedades de publicación se controlan en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde el **publicar**, **seguridad**, y **firma** páginas de propiedades de la **Diseñador de proyectos** . A continuación se muestra una descripción de las propiedades de publicación, junto con un valor que indica cómo cada uno de ellos se establece en las diversas páginas de propiedades del Diseñador de aplicaciones:  
  
-   `AssemblyOriginatorKeyFile`Determina el archivo clave utilizado para firmar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos de aplicación. Esta misma clave también puede utilizarse para asignar un nombre seguro a los ensamblados. Esta propiedad está establecida en el **firma** página de la **Diseñador de proyectos**.  
  
 Las siguientes propiedades se establecen en los **seguridad** página:  
  
-   **Habilitar la configuración de seguridad de ClickOnce** determina si [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se generan los manifiestos. Cuando un proyecto se crea inicialmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generación del manifiesto está desactivada de forma predeterminada. El asistente convertirá automáticamente este indicador cuando publique por primera vez.  
  
-   **TargetZone** determina el nivel de confianza puede emitir en su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Los valores posibles son "Internet", "Intranet local" y "Custom". Internet e intranet local provocará un conjunto de permisos predeterminado puede emitir en su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Intranet local es el valor predeterminado y básicamente significa plena confianza. Custom indica que sólo los permisos especificados explícitamente en el archivo app.manifest base se puede emitir en el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. El archivo app.manifest es un archivo de manifiesto parcial que contiene solo las definiciones de la información de confianza. Es un archivo oculto, se agrega automáticamente al proyecto cuando se configuren permisos en el **seguridad** página.  
  
 Las siguientes propiedades se establecen en los **publicar** página:  
  
-   `PublishUrl`es la ubicación donde se publicará la aplicación en el IDE. Se inserta en la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación si no la `InstallUrl` o `UpdateUrl` se especifica la propiedad.  
  
-   `ApplicationVersion`Especifica la versión de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Se trata de un número de versión de cuatro dígitos. Si el último dígito es un "*", la `ApplicationRevision` se sustituye por el valor insertado en el manifiesto en tiempo de compilación.  
  
-   `ApplicationRevision`Especifica la revisión. Se trata de un entero que se incrementa cada vez que publique en el IDE. Tenga en cuenta que no se incrementa automáticamente para las compilaciones realizadas desde la línea de comandos.  
  
-   `Install`Determina si la aplicación es una aplicación instalada o una aplicación de ejecución desde el Web.  
  
-   `InstallUrl`(no se muestra) es la ubicación donde los usuarios instalarán la aplicación de. Si se especifica, este valor se graba en el programa previo de setup.exe si el `IsWebBootstrapper` propiedad está habilitada. También se inserta en la aplicación de manifiesto si la `UpdateUrl` no se ha especificado.  
  
-   `SupportUrl`la ubicación (no mostrado) está vinculada a la **agregar o quitar programas** cuadro de diálogo para una aplicación instalada.  
  
 Las siguientes propiedades se establecen en los **actualizaciones de la aplicación** cuadro de diálogo, tiene acceso desde el **publicar** página.  
  
-   `UpdateEnabled`indica si la aplicación debe buscar actualizaciones.  
  
-   `UpdateMode`Especifica las actualizaciones de primer plano o actualizaciones en segundo plano.  
  
-   `UpdateInterval`Especifica la frecuencia con la que la aplicación buscará actualizaciones.  
  
-   `UpdateIntervalUnits`Especifica si la `UpdateInterval` valor está en unidades de horas, días o semanas.  
  
-   `UpdateUrl`(no se muestra) es la ubicación desde la que la aplicación recibirá actualizaciones. Si se especifica, este valor se inserta en el manifiesto de aplicación.  
  
-   Las siguientes propiedades se establecen en los **opciones de publicación** cuadro de diálogo, tiene acceso desde el **publicar** página.  
  
-   `PublisherName`Especifica el nombre del publicador que se muestra en el símbolo del sistema que se muestra cuando se instala o ejecuta la aplicación. En el caso de una aplicación instalada, también se utiliza para especificar el nombre de la carpeta en la **iniciar** menú.  
  
-   `ProductName`Especifica el nombre del producto que se muestran en el símbolo del sistema que se muestra cuando se instala o ejecuta la aplicación. En el caso de una aplicación instalada, también se utiliza para especificar el nombre de método abreviado en el **iniciar** menú.  
  
-   Las siguientes propiedades se establecen en los **requisitos previos** cuadro de diálogo, tiene acceso desde el **publicar** página.  
  
-   `BootstrapperEnabled`Determina si se debe generar al programa previo de setup.exe.  
  
-   `IsWebBootstrapper`Determina si el programa previo de setup.exe funciona a través de Internet o en modo basado en disco.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL y UpdateURL  
 La tabla siguiente muestran las cuatro opciones de dirección URL para la implementación ClickOnce.  
  
|Opción de dirección URL|Descripción|  
|----------------|-----------------|  
|`PublishURL`|Necesario si va a publicar la aplicación ClickOnce para un sitio Web.|  
|`InstallURL`|Opcional. Establezca esta opción de dirección URL si el sitio de instalación es diferente de la `PublishURL`. Por ejemplo, podría establecer el `PublishURL` a una ruta de acceso FTP y establezca el `InstallURL` a una dirección URL Web.|  
|`SupportURL`|Opcional. Establezca esta opción de dirección URL si el sitio de soporte técnico es diferente de la `PublishURL`. Por ejemplo, podría establecer el `SupportURL` al sitio de Web de atención al cliente de su empresa.|  
|`UpdateURL`|Opcional. Establezca esta opción de dirección URL si la ubicación de actualización es diferente de la `InstallURL`. Por ejemplo, podría establecer el `PublishURL` a una ruta de acceso FTP y establezca el `UpdateURL` a una dirección URL Web.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
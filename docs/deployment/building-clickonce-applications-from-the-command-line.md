---
title: "Compilar aplicaciones ClickOnce desde la l&#237;nea de comandos | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, desde la línea de comandos"
  - "publicar"
  - "publicar, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Compilar aplicaciones ClickOnce desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] puede compilar proyectos desde la línea de comandos aunque se hayan creado en el entorno de desarrollo integrado \(IDE\).  De hecho, puede recompilar un proyecto creado con [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] en otro equipo que tenga sólo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] instalado.  Esto le permitirá reproducir una compilación mediante un proceso automatizado, por ejemplo, en un laboratorio de compilación central o mediante técnicas avanzadas de scripting sin limitarse únicamente a compilar el proyecto en sí.  
  
## Usar MSBuild para reproducir las implementaciones de las aplicaciones ClickOnce  
 Al escribir msbuild \/target:publish en la línea de comandos, se indica al sistema MSBuild que compile el proyecto y cree una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en la carpeta de publicación.  Esto equivale a seleccionar el comando **Publicar** en el IDE.  
  
 Este comando ejecuta msbuild.exe, que está en la ruta de acceso del entorno de símbolo del sistema de Visual Studio.  
  
 Un "destino" es un indicador para MSBuild acerca de cómo procesar el comando.  Los destinos clave son el destino de "compilación" y el de "publicación".  El destino de compilación es el equivalente a seleccionar el comando Build \(o presionar F5\) en el IDE.  Si sólo desea compilar su proyecto, escriba `msbuild`.  Este comando funciona porque el destino de compilación es el destino predeterminado para todos los proyectos generados por [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Esto significa que no es necesario especificar explícitamente el destino de la compilación.  Por consiguiente, escribir `msbuild` es la misma operación que escribir `msbuild /target:build`.  
  
 El comando `/target:publish` indica a MSBuild que invoque el destino de publicación.  El destino de publicación depende del destino de compilación.  Esto significa que la operación de publicación es un supraconjunto de la operación de compilación.  Por ejemplo, si realizara un cambio en uno de sus archivos de código fuente de Visual Basic o C\#, el ensamblado correspondiente sería recompilado automáticamente por la operación de publicación.  
  
 Para obtener información acerca de cómo generar una implementación completa de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizando la herramienta de línea de comandos Mage.exe para crear su manifiesto de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Crear y compilar una aplicación ClickOnce de Basic con MSBuild  
  
#### Para crear y publicar un proyecto de ClickOnce  
  
1.  Haga clic en **Nuevo proyecto** en el menú **Archivo**.  Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
2.  Seleccione **Aplicación para Windows** y asígnele el nombre `CmdLineDemo`.  
  
3.  En el menú **Compilar**, haga clic en el comando **Publicar**.  
  
     Este paso asegura que el proyecto está correctamente configurado para generar una implementación de aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
     Aparece el Asistente para publicación.  
  
4.  En el Asistente para publicación, haga clic en **Finalizar**.  
  
     Visual Studio genera y muestra la página Web predeterminada, denominada Publish.htm.  
  
5.  Guarde su proyecto y anote la ubicación de la carpeta en la que se almacena.  
  
 Los pasos anteriores crean un proyecto de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que se ha publicado por primera vez.  Ahora se puede reproducir la compilación fuera del IDE.  
  
#### Para reproducir la compilación desde la línea de comandos  
  
1.  Salga de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  En el menú **Inicio** de Windows, haga clic en **Todos los programas**, en **Microsoft Visual Studio 2008**, en **Visual Studio Tools** y, a continuación, en **Símbolo del sistema de Visual Studio**.  Esto debe abrir un símbolo del sistema en la carpeta raíz del usuario actual.  
  
3.  En el **Símbolo del sistema de Visual Studio**, cambie el directorio actual a la ubicación del proyecto que compiló anteriormente.  Por ejemplo, escriba `chdir Mis Documentos\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Para quitar los archivos existentes generados en "Para crear y publicar un proyecto de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ", escriba `rmdir /s publish`.  
  
     Este paso es opcional, pero garantiza que todos los archivos nuevos fueron creados por el sistema de compilación de línea de comandos.  
  
5.  Escriba `msbuild /target: publish`.  
  
 Los pasos anteriores generarán una implementación de aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completa en una subcarpeta del proyecto denominada **Publish**.  CmdLineDemo.application es el manifiesto de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La carpeta CmdLineDemo\_1.0.0.0 contiene los archivos CmdLineDemo.exe y CmdLineDemo.exe.manifest, el manifiesto de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Setup.exe es el arranque, que de manera predeterminada está configurado para instalar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  La carpeta DotNetFX contiene los archivos redistribuibles para [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Éste es el conjunto de archivos completo que necesita para implementar su aplicación en el Web o mediante UNC o CD\/DVD.  
  
## Propiedades de publicación  
 Al publicar la aplicación siguiendo los procedimientos anteriores, el Asistente para publicación inserta las propiedades siguientes en el archivo de proyecto.  Estas propiedades influyen directamente en cómo se genera la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 En CmdLineDemo.vbproj \/ CmdLineDemo.csproj:  
  
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
  
 Puede reemplazar cualquiera de estas propiedades en la línea de comandos sin modificar el propio archivo de proyecto.  Por ejemplo, el texto siguiente compilará la implementación de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sin el arranque:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Las propiedades de publicación se controlan en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde las páginas de propiedades **Publicar**, **Seguridad** y **Firma** del **Diseñador de proyectos**.  A continuación se incluye una descripción de las propiedades de publicación, junto con una indicación de cómo se establece cada una en las diversas páginas de propiedades del diseñador de aplicaciones:  
  
-   `AssemblyOriginatorKeyFile` determina el archivo clave utilizado para firmar sus manifiestos de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Esta misma clave se puede utilizar también para asignar un nombre seguro a sus ensamblados.  Esta propiedad se establece en la página **Firma** del **Diseñador de proyectos**.  
  
 Las propiedades siguientes se establecen en la página **Seguridad**:  
  
-   **Habilitar configuración de seguridad de ClickOnce** determina si se generan manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cuando se crea un proyecto inicialmente, la generación de manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] está desactivada de manera predeterminada.  El asistente activará automáticamente este marcador cuando publique por primera vez.  
  
-   **TargetZone** determina el nivel de confianza que se va a emitir en su manifiesto de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Los valores posibles son "Internet", "LocalIntranet" y "Custom".  Internet y LocalIntranet producirán un conjunto de permisos predeterminado que se emitirá en su manifiesto de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  LocalIntranet es el valor predeterminado y básicamente significa plena confianza.  Custom indica que sólo los permisos especificados explícitamente en el archivo app.manifest base se emitirán en el manifiesto de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  El archivo app.manifest es un archivo de manifiesto parcial que contiene simplemente las definiciones de información de confianza.  Es un archivo oculto que se agrega automáticamente al proyecto cuando se configuran los permisos en la página **Seguridad**.  
  
 Las propiedades siguientes se establecen en la página **Publicar**:  
  
-   `PublishUrl` es la ubicación donde se publicará la aplicación en el IDE.  Se inserta en el manifiesto de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si no se especifica la propiedad `InstallUrl` o `UpdateUrl`.  
  
-   `ApplicationVersion` especifica la versión de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Éste es un número de versión de cuatro dígitos.  Si el último dígito es "\*", `ApplicationRevision` se sustituye por el valor insertado en el manifiesto durante la compilación.  
  
-   `ApplicationRevision` especifica la revisión.  Se trata de un número entero que se incrementará cada vez que publique en el IDE.  Observe que no se incrementa automáticamente para las compilaciones realizadas desde la línea de comandos.  
  
-   `Install` determina si la aplicación es una aplicación instalada o una aplicación de ejecución en Web.  
  
-   `InstallUrl` \(no se muestra\) es la ubicación desde donde los usuarios instalarán la aplicación.  Si especificó algún valor, éste se grabará en el arranque de setup.exe si está habilitada la propiedad `IsWebBootstrapper`.  También se inserta en el manifiesto de la aplicación si no se especifica la propiedad `UpdateUrl`.  
  
-   `SupportUrl` \(no se muestra\) es la ubicación vinculada en el cuadro de diálogo **Agregar o quitar programas** para una aplicación instalada.  
  
 Las propiedades siguientes se establecen en el cuadro de diálogo **Actualizaciones de la aplicación**, a las que se tiene acceso desde la página **Publicar**.  
  
-   `UpdateEnabled` indica si la aplicación debe comprobar o no la existencia de actualizaciones.  
  
-   `UpdateMode` especifica que las actualizaciones sean de primer plano o de fondo.  
  
-   `UpdateInterval` especifica la frecuencia con qué la aplicación debe comprobar si existen actualizaciones.  
  
-   `UpdateIntervalUnits` especifica si el valor de `UpdateInterval` está en unidades de horas, días o semanas.  
  
-   `UpdateUrl` \(no se muestra\) es la ubicación desde la que la aplicación recibirá las actualizaciones.  Si especificó algún valor, éste se insertará en el manifiesto de la aplicación.  
  
-   Las propiedades siguientes se establecen en el cuadro de diálogo **Opciones de publicación**, a las que se tiene acceso desde la página **Publicar**.  
  
-   `PublisherName` especifica el nombre del editor mostrado en el indicador que aparece al instalar o ejecutar la aplicación.  En el caso de una aplicación instalada, se utiliza también para especificar el nombre de la carpeta en el menú **Inicio**.  
  
-   `ProductName` especifica el nombre del producto mostrado en el indicador que aparece al instalar o ejecutar la aplicación.  En el caso de una aplicación instalada, se utiliza también para especificar el nombre del acceso directo que aparecerá en el menú **Inicio**.  
  
-   Las propiedades siguientes se establecen en el cuadro de diálogo **Requisitos previos**, al que se tiene acceso desde la página **Publicar**.  
  
-   `BootstrapperEnabled` determina si generar o no el arranque de setup.exe.  
  
-   `IsWebBootstrapper` determina si el arranque de setup.exe funciona sobre el Web o en modo basado en discos.  
  
## InstallURL, SupportUrl, PublishURL y UpdateURL  
 En la siguiente tabla, se muestran las cuatro opciones de dirección URL para la implementación ClickOnce.  
  
|Opción de dirección URL|Descripción|  
|-----------------------------|-----------------|  
|`PublishURL`|Se requiere si se publica la aplicación ClickOnce en un sitio web.|  
|`InstallURL`|Opcional.  Establezca esta opción de dirección URL si el sitio de instalación es diferente de `PublishURL`.  Por ejemplo, puede establecer `PublishURL` en una ruta de acceso de FTP e `InstallURL` en una Dirección URL de Web.|  
|`SupportURL`|Opcional.  Establezca esta opción de dirección URL si el sitio de soporte es diferente de `PublishURL`.  Por ejemplo, podría establecer el valor de `SupportURL` en el sitio web de soporte al cliente de su compañía.|  
|`UpdateURL`|Opcional.  Establezca esta opción de dirección URL si la ubicación de actualización es diferente de `InstallURL`.  Por ejemplo, puede establecer `PublishURL` en una ruta de acceso de FTP e `UpdateURL` en una Dirección URL de Web.|  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
---
title: "Seguridad e implementaci&#243;n ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce"
  - "implementar aplicaciones [ClickOnce]"
  - "publicar, ClickOnce"
  - "aplicaciones Windows, implementación ClickOnce"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Seguridad e implementaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es una tecnología de implementación que permite crear aplicaciones basadas en Windows de actualización automática, que se pueden instalar y ejecutar con interacción mínima por parte del usuario. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona compatibilidad completa para publicar y actualizar aplicaciones implementadas con tecnología ClickOnce si ha desarrollado los proyectos con Visual Basic y Visual C\#.  Para obtener información acerca de la implementación de aplicaciones de Visual C\+\+, consulte [Implementación de ClickOnce para aplicaciones de Visual C\+\+](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 La implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supera tres problemas importantes de la implementación:  
  
-   **Dificultades para actualizar las aplicaciones.** Con la implementación de Microsoft Windows Installer, siempre que se actualice una aplicación, el usuario puede instalar una actualización, un archivo msp, y aplicarla al producto instalado; con la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], es posible proporcionar actualizaciones automáticamente.  Sólo se descargan las partes de la aplicación que hayan cambiado y, a continuación, la aplicación completa y actualizada vuelve a instalarse desde una nueva carpeta en paralelo.  
  
-   **Impacto en el equipo del usuario.** Con la implementación de Windows Installer, las aplicaciones normalmente utilizan componentes compartidos, con sus posibles conflictos de versiones; gracias a la implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], cada aplicación es autosuficiente y no puede interferir con otras aplicaciones.  
  
-   **Permisos de seguridad.** La implementación de Windows Installer requiere permisos administrativos y sólo permite una instalación de usuario limitada; la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] habilita a los usuarios que no tienen derechos administrativos para realizar la instalación y sólo concede los permisos de seguridad de acceso del código necesarios para la aplicación.  
  
 Antes, estos problemas hacían que los desarrolladores decidieran crear aplicaciones web en lugar de aplicaciones basadas en Windows, sacrificando la interfaz de usuario enriquecida que posibilita una instalación más fácil.  Con aplicaciones implementadas mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], puede aprovechar lo mejor de ambas tecnologías.  
  
## ¿Qué es una aplicación ClickOnce?  
 Una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es cualquier aplicación de Windows Presentation Foundation \(.xbap\), de Windows Forms \(.exe\) o de consola \(.exe\) o una solución de Office \(.dll\) publicada mediante la tecnología [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Puede publicar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de tres maneras distintas: desde una página web, desde un recurso compartido de archivos de red o desde otros medios como un CD\-ROM.  Una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se puede instalar en el equipo de un usuario final y ejecutarse localmente incluso cuando el equipo está trabajando sin conexión, o bien, se puede ejecutar solo en línea sin instalar nada de manera permanente en el equipo del usuario final.  Para obtener más información, vea [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se pueden actualizar automáticamente; pueden comprobar si hay versiones más recientes cuando se publican y reemplazar automáticamente los archivos actualizados.  El desarrollador puede especificar el comportamiento de actualización; los administradores de red también pueden controlar las estrategias de actualización, por ejemplo, marcando una actualización como obligatoria.  El usuario final o un administrador también pueden revertir las actualizaciones a una versión anterior.  Para obtener más información, vea [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Dado que las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] están aisladas, la instalación o ejecución de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no interrumpe las aplicaciones existentes.  Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] son autónomas; cada aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se instala y se ejecuta en una memoria caché por usuario y por aplicación segura.  Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se ejecutan en las zonas de seguridad de Internet o Intranet.  Si necesario, la aplicación puede solicitar permisos de seguridad elevados.  Para obtener más información, vea [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Cómo funciona la seguridad ClickOnce  
 La seguridad [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] básica está basada en certificados, directivas de seguridad de acceso del código y el indicador confiable de ClickOnce.  
  
### Certificados  
 Los certificados Authenticode se utilizan para comprobar la autenticidad del publicador de la aplicación.  Utilizando Authenticode para la implementación de aplicaciones, ClickOnce ayuda a evitar que un programa dañino se presente como un programa legítimo que viene de un origen establecido, de confianza.  Opcionalmente, los certificados también se pueden utilizar para firmar los manifiestos de implementación y aplicación para demostrar que los archivos no han sido manipulados.  Para obtener más información, vea [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md).  Los certificados también se pueden utilizar para configurar los equipos cliente para tener una lista de publicadores de confianza.  Si una aplicación procede de un publicador de confianza, se puede instalar sin ninguna interacción con el usuario.  Para obtener más información, vea [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
### Seguridad de acceso del código  
 La seguridad de acceso del código ayuda a limitar el acceso que tiene el código a los recursos protegidos.  En la mayoría de los casos, puede utilizar las zonas de Internet o intranet local para limitar los permisos.  Utilice la página **Seguridad** del **Diseñador de proyectos** para solicitar la zona adecuada de la aplicación.  También puede depurar las aplicaciones con permisos restringidos para emular la experiencia de usuario final.  Para obtener más información, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### Mensaje relativo a la confianza de ClickOnce  
 Si la aplicación solicita más permisos de los que la zona permite, es posible que se solicite al usuario final que tome una decisión de confianza.  El usuario final puede decidir si las aplicaciones ClickOnce, como las aplicaciones de Windows Forms, de Windows Presentation Foundation, de consola, de explorador XAML y soluciones de Office son de confianza.  Para obtener más información, vea [Cómo: Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Cómo funciona la implementación ClickOnce  
 La arquitectura central de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se basa en dos archivos de manifiesto XML: un manifiesto de aplicación y un manifiesto de implementación.  Los archivos se utilizan para describir de dónde se instalan las aplicaciones ClickOnce, cómo se actualizan y cuándo están actualizadas.  
  
### Publicar aplicaciones ClickOnce  
 El manifiesto de aplicación describe la aplicación en sí.  Incluye los ensamblados, las dependencias y los archivos que constituyen la aplicación, los permisos necesarios y la ubicación en que estarán disponibles las actualizaciones.  El desarrollador de aplicaciones crea el manifiesto de aplicación utilizando el Asistente para publicación de Visual Studio o la herramienta de generación y edición de manifiestos \(Mage.exe\) de [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Para obtener más información, vea [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 El manifiesto de implementación describe cómo se implementa la aplicación.  Esto incluye la ubicación del manifiesto de aplicación y la versión de la aplicación que los clientes deben ejecutar.  
  
### Implementar las aplicaciones ClickOnce  
 Una vez creado, el manifiesto de implementación se copia en la ubicación de implementación.  Ésta puede ser un servidor Web, un recurso compartido de archivos de red u otros medios como un CD.  El manifiesto de aplicación y todos los archivos de la aplicación también se copian en una ubicación de implementación que se especifica en el manifiesto de implementación.  Ésta puede ser la misma que la ubicación de implementación o una ubicación diferente.  Al utilizar el **Asistente para publicación** de Visual Studio, las operaciones de copia se realizan automáticamente.  
  
### Instalar aplicaciones ClickOnce  
 Una vez implementado en la ubicación de implementación, los usuarios finales pueden descargar e instalar la aplicación haciendo clic en un icono que representa el archivo de manifiesto de implementación que se incluya en una página Web o en una carpeta.  En la mayoría de los casos, se presenta al usuario final un cuadro de diálogo sencillo que le pide que confirme la instalación, tras lo cual la instalación continúa y la aplicación se inicia sin necesidad de ninguna intervención posterior.  En los casos en los que la aplicación requiere permisos elevados o no está firmada por un certificado de confianza, el cuadro de diálogo también le pide al usuario que conceda permiso para que pueda continuar la instalación.  Aunque las instalaciones de ClickOnce son por usuario, se puede requerir la elevación de permisos si existen requisitos previos que requieren privilegios de administrador.  Para obtener más información sobre permisos elevados, vea [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Los certificados pueden ser de confianza en el nivel de equipo o de empresa, para que las aplicaciones ClickOnce firmadas con un certificado de confianza se puede instalar en modo silencioso.  Para obtener más información sobre el uso de certificados de confianza, consulte [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
 La aplicación se puede agregar al menú **Inicio** del usuario y al grupo **Agregar o quitar programas** del **Panel de control**.  A diferencia de otras tecnologías de implementación, no se agrega nada a la carpeta **Archivos de programa** ni al Registro, y no se requieren derechos de administración para realizar la instalación.  
  
> [!NOTE]
>  También es posible impedir que la aplicación se agregue al menú **Inicio** y al grupo **Agregar o quitar programas**, haciendo que de hecho se comporte como una aplicación web.  Para obtener más información, vea [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### Actualizar las aplicaciones ClickOnce  
 Cuando el desarrollador de aplicaciones crea una versión actualizada de la aplicación, también genera un nuevo manifiesto de aplicación y copia archivos en una ubicación de implementación, normalmente una carpeta relacionada con la carpeta original de implementación de la aplicación.  El administrador actualiza el manifiesto de implementación para que señale a la ubicación de la nueva versión de la aplicación.  
  
> [!NOTE]
>  El **Asistente para publicación** de Visual Studio se puede utilizar para realizar estos pasos.  
  
 Además de la ubicación de implementación, el manifiesto de implementación también contiene una ubicación de actualizaciones \(una página web o recurso compartido de archivos de red\) donde la aplicación comprueba si hay versiones actualizadas.  Las propiedades **Publish** de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se utilizan para especificar cuándo y con qué frecuencia la aplicación debe comprobar si hay actualizaciones.  El comportamiento de actualización se puede especificar en el manifiesto de implementación o se puede presentar como opciones del usuario en la interfaz de usuario de la aplicación por medio de las API de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Además, las propiedades **Publish** se pueden emplear para que las actualizaciones sean obligatorias o revertir a una versión anterior.  Para obtener más información, vea [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### Instaladores de otros fabricantes  
 Puede personalizar el instalador de ClickOnce para instalar componentes de otros fabricantes junto con su aplicación.  Debe tener el paquete redistribuible \(archivo .exe o .msi\) y describirlo con un manifiesto de producto independiente del idioma y un manifiesto de paquete específico del idioma.  Para obtener más información, vea [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
## Herramientas ClickOnce  
 En la siguiente tabla se muestran las herramientas que puede utilizar para generar, modificar, firmar y volver a firmar los manifiestos de implementación y aplicación.  
  
|Herramienta|Descripción|  
|-----------------|-----------------|  
|[Página Seguridad, Diseñador de proyectos](../ide/reference/security-page-project-designer.md)|Firma los manifiestos de aplicación e implementación.|  
|[Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)|Genera y edita los manifiestos de implementación y aplicación para aplicaciones de Visual Basic y Visual C\#.|  
|[Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|Genera los manifiestos de implementación y aplicación para aplicaciones de Visual Basic, C\# y Visual C\+\+.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar a partir de scripts por lotes y el símbolo del sistema.|  
|[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|Genera y modifica los manifiestos de aplicación e implementación.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.|  
|[GenerateApplicationManifest \(Tarea\)](../msbuild/generateapplicationmanifest-task.md)|Genera el manifiesto de aplicación.<br /><br /> Se puede ejecutar desde MSBuild.  Para obtener más información, vea [Referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest \(Tarea\)](../msbuild/generatedeploymentmanifest-task.md)|Genera el manifiesto de implementación.<br /><br /> Se puede ejecutar desde MSBuild.  Para obtener más información, vea [Referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[SignFile \(Tarea\)](../msbuild/signfile-task.md)|Firma los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar desde MSBuild.  Para obtener más información, vea [Referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Desarrolle su propia aplicación para generar los manifiestos de implementación y aplicación.|  
  
 En la siguiente tabla se muestra la versión de .NET Framework requerida para las aplicaciones ClickOnce en estos exploradores.  
  
|Browser|Versión de .NET Framework|  
|-------------|-------------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## Vea también  
 [Implementación de ClickOnce en Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implementar componentes COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilar aplicaciones ClickOnce desde la línea de comandos](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
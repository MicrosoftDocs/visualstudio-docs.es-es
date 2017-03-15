---
title: "ClickOnce y configuraci&#243;n de la aplicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "implementación ClickOnce, configuración de la aplicación"
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce y configuraci&#243;n de la aplicaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La configuración de aplicaciones para formularios Windows Forms facilita la creación, el almacenamiento y el mantenimiento de preferencias de usuarios y aplicaciones personalizadas en el cliente.  El documento siguiente describe cómo trabajan los archivos de configuración en una aplicación de ClickOnce y cómo migra ClickOnce la configuración cuando el usuario realiza la actualización a la siguiente versión.  
  
 La información siguiente sólo se aplica al proveedor de configuración de aplicación predeterminado, la clase <xref:System.Configuration.LocalFileSettingsProvider>.  Si proporciona un proveedor personalizado, ese proveedor determinará cómo almacena sus datos y cómo actualiza su configuración de unas versiones a otras.  Para obtener más información sobre los proveedores de configuración de aplicación, vea [Application Settings Architecture](../Topic/Application%20Settings%20Architecture.md).  
  
## Archivos de configuración de aplicación  
 La configuración de una aplicación usa dos archivos: *aplicación*.exe.config y user.config, donde *aplicación* es el nombre de la aplicación de Windows Forms.  El archivo user.config se crea en el cliente la primera vez que la aplicación almacena la configuración con ámbito de usuario.  Sin embargo, el archivo *aplicación*.exe.config existirá antes de la implementación si se definen valores predeterminados para la configuración.  Visual Studio incluirá automáticamente este archivo cuando se utiliza su comando **Publicar**.  Si crea su aplicación ClickOnce mediante Mage.exe o MageUI.exe, debe asegurarse de que este archivo se incluye con los otros archivos de su aplicación cuando rellene su manifiesto de aplicación.  
  
 En una aplicación de formularios Windows Forms no implementada con ClickOnce, el archivo *aplicación*.exe.config se almacena en el directorio de aplicación, mientras que el archivo user.config se almacena en la carpeta **Documents and Settings** del usuario.  En una aplicación ClickOnce, *aplicación*.exe.config se encuentra en el directorio de la aplicación dentro de la caché de la aplicación ClickOnce, mientras que user.config reside en el directorio de datos de ClickOnce para esa aplicación.  
  
 Independientemente de cómo se implemente la aplicación, la configuración de la misma garantiza el acceso de lectura seguro a *aplicación*.exe.config y el acceso de lectura y escritura seguro a user.config.  
  
 En una aplicación ClickOnce, el tamaño de los archivos de configuración usados por la configuración de aplicación está limitado por el tamaño de la caché de ClickOnce.  Para obtener más información, vea [Información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## Actualizaciones de versiones  
 Al igual que cada versión de una aplicación ClickOnce está aislada de todas las demás versiones, los ajustes de configuración de una aplicación ClickOnce también están aislados de la configuración de otras versiones.  Cuando su usuario actualice a una versión posterior de su aplicación, la configuración de la aplicación compara los ajustes de la versión más reciente \(la del número más alto\) con los ajustes proporcionados con la versión actualizada y combina los ajustes en un nuevo conjunto de archivos de configuración.  
  
 La tabla siguiente describe cómo la configuración de la aplicación decide qué ajustes copiar.  
  
|Tipo de cambio|Acción de actualización|  
|--------------------|-----------------------------|  
|Valor de configuración agregado a *aplicación*.exe.config|La nueva configuración se combina en el archivo *aplicación*.exe.config de la versión actual|  
|Valor de configuración quitado de *aplicación*.exe.config|La configuración anterior se quita del archivo *aplicación*.exe.config de la versión actual|  
|Cambiado el valor predeterminado del ajuste; el ajuste local todavía está ajustado en el valor predeterminado original de user.config|El ajuste se combina en el archivo user.config de la versión actual con el nuevo valor predeterminado como el valor|  
|Se cambia el valor predeterminado del ajuste; el ajuste se establece en un valor no predeterminado en el archivo user.config|El ajuste se combina en el archivo user.config de la versión actual manteniendo el valor no predeterminado|  
  
 Si ha creado su propia clase contenedora de configuración de aplicación y desea personalizar la lógica de actualización, puede reemplazar el método <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>.  
  
## Configuración de ClickOnce y movilidad  
 ClickOnce no funciona con configuración de movilidad, que permite a su archivo de configuración seguirle por los distintos equipos de una red.  Si necesita ajustes en movilidad, deberá implementar un proveedor de configuración de aplicación que almacene la configuración en la red o desarrollar sus propias clases de configuración personalizadas para almacenar la configuración en un equipo remoto.  Para obtener más información sobre los proveedores de configuración, vea [Application Settings Architecture](../Topic/Application%20Settings%20Architecture.md).  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Introducción a la configuración de la aplicación](../Topic/Application%20Settings%20Overview.md)   
 [Información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
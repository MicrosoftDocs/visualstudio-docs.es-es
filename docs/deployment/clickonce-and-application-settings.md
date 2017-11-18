---
title: "ClickOnce y configuración de la aplicación | Documentos de Microsoft"
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
helpviewer_keywords: ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fbe35de06ac09c95a045748a5d8ecb379779a20a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-and-application-settings"></a>ClickOnce y configuración de la aplicación
Configuración de la aplicación de Windows Forms facilita la crear, almacenar y mantener aplicaciones personalizadas y las preferencias del usuario en el cliente. El siguiente documento describe cómo funcionan los archivos de configuración de la aplicación en una aplicación ClickOnce y cómo migra ClickOnce la configuración cuando el usuario realiza una actualización a la versión siguiente.  
  
 La siguiente información se aplica solo para el proveedor de configuración de aplicación predeterminado, el <xref:System.Configuration.LocalFileSettingsProvider> clase. Si se proporciona un proveedor personalizado, ese proveedor determinará cómo almacena sus datos y cómo actualiza su configuración entre versiones. Para obtener más información sobre los proveedores de configuración de aplicaciones, consulte [Application Settings Architecture](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Archivos de configuración de la aplicación  
 Configuración de la aplicación consume los dos archivos: *aplicación*. exe.config y user.config, donde *aplicación* es el nombre de la aplicación de formularios Windows Forms. el archivo User.config se crea en el cliente la primera vez que la aplicación almacena la configuración de ámbito de usuario. *aplicación*. exe.config, por el contrario, existirá antes de la implementación si define valores predeterminados de configuración. Visual Studio incluirá este archivo automáticamente cuando se usa su **publicar** comando. Si crea la aplicación ClickOnce mediante Mage.exe o MageUI.exe, debe asegurarse de que este archivo se incluye con la aplicación de otros archivos al rellenar el manifiesto de aplicación.  
  
 En aplicaciones de Windows Forms no implementada con ClickOnce, una aplicación *aplicación*. exe.config archivo se almacena en el directorio de la aplicación, mientras que el archivo user.config se almacena en el usuario **Documents and Settings**  carpeta. En una aplicación ClickOnce, *aplicación*. exe.config se encuentra en el directorio de la aplicación dentro de la caché de aplicación de ClickOnce y user.config reside en el directorio de datos de ClickOnce para esa aplicación.  
  
 Independientemente de cómo implementar la aplicación, configuración de la aplicación garantiza el acceso de lectura seguro a *aplicación*. exe.config y acceso de lectura y escritura seguro a user.config.  
  
 En una aplicación ClickOnce, el tamaño de los archivos de configuración usados por la configuración de la aplicación está limitado por el tamaño de la caché de ClickOnce. Para obtener más información, consulte [información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Actualizaciones de versión  
 Al igual que todas las versiones de una aplicación ClickOnce se aísla de todas las demás versiones, la configuración de la aplicación para una aplicación ClickOnce está aislada de la configuración de otras versiones también. Cuando el usuario realiza una actualización a una versión posterior de la aplicación, configuración de la aplicación compara configuración más reciente (con el número mayor) de la versión en los valores proporcionados con la versión actualizada y combina los ajustes en un nuevo conjunto de archivos de configuración.  
  
 En la tabla siguiente describe la configuración de la aplicación decide qué opciones de configuración para copiar.  
  
|Tipo de cambio|Acción de actualización|  
|--------------------|--------------------|  
|Ajuste agregado a *aplicación*. exe.config|La nueva configuración se combina con la versión actual *aplicación*. exe.config|  
|Configuración de quitarla *aplicación*. exe.config|La configuración anterior se quita de la versión actual *aplicación*. exe.config|  
|Valor predeterminado de la configuración que ha cambiado; configuración local sigue establecido valores predeterminados originales en el archivo user.config|La configuración se combina en el archivo user.config de la versión actual con el nuevo valor predeterminado como el valor|  
|Valor predeterminado de la configuración que ha cambiado; valor establecido en no predeterminado en el archivo user.config|La configuración se combina en el archivo user.config de la versión actual con el valor no predeterminado que se conservan|  
  
 Si ha creado su propia configuración de la aplicación clase contenedora y desea personalizar la lógica de actualización, se puede invalidar el <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> método.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce y configuración móvil  
 ClickOnce no funciona con la configuración de roaming, lo que permite al archivo de configuración debe seguir en los equipos en una red. Si necesita la configuración de roaming, debe implementar un proveedor de configuración de aplicación que almacena la configuración a través de la red o desarrollar sus propias clases de configuración personalizada para almacenar la configuración en un equipo remoto. Para obtener más información en los proveedores de configuración, consulte [Application Settings Architecture](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Introducción a la configuración de la aplicación](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Información general de la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
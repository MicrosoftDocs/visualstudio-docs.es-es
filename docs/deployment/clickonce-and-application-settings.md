---
title: ClickOnce y configuración de la aplicación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40077a30a49842187c24b4cf8b0cba18b3d0a46a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850971"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce y configuración de la aplicación
Configuración de la aplicación para Windows Forms facilita crear, almacenar y mantener aplicaciones personalizadas y las preferencias del usuario en el cliente. El siguiente documento describe cómo funcionan los archivos de configuración de aplicación en una aplicación ClickOnce y cómo ClickOnce migra la configuración cuando el usuario realiza una actualización a la siguiente versión.  
  
 La siguiente información se aplica solo para el proveedor de configuración de aplicación predeterminado, el \<xref:System.Configuration.LocalFileSettingsProvider > clase. Si se proporciona un proveedor personalizado, ese proveedor determinará cómo almacena sus datos y cómo actualiza la configuración entre versiones. Para obtener más información sobre los proveedores de configuración de aplicación, consulte [arquitectura de configuración de aplicación](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Archivos de configuración de aplicación  
 Configuración de la aplicación consume los dos archivos:  *\<aplicación >. exe.config* y *user.config*, donde *aplicación* es el nombre de la aplicación de Windows Forms. *el archivo User.config* se crea en el cliente la primera vez que la aplicación almacena la configuración de ámbito de usuario. *\<aplicación >. exe.config*, por el contrario, existirá antes de la implementación si define los valores predeterminados para la configuración. Visual Studio incluirá este archivo automáticamente cuando se usa su **publicar** comando. Si crea su aplicación ClickOnce mediante *Mage.exe* o *MageUI.exe*, debe asegurarse de que este archivo se incluye con la aplicación de otros archivos al rellenar el manifiesto de aplicación.  
  
 En aplicaciones no implementadas con ClickOnce, una aplicación Windows Forms  *\<aplicación >. exe.config* archivo se almacena en el directorio de la aplicación, mientras que el *user.config* se almacena el archivo en el usuario **Documents and Settings** carpeta. En una aplicación ClickOnce,  *\<aplicación >. exe.config* reside en el directorio de la aplicación dentro de la caché de la aplicación ClickOnce, y *user.config* reside en el directorio de datos de ClickOnce para esa aplicación.  
  
 Independientemente de cómo implementar la aplicación, configuración de la aplicación garantiza el acceso de lectura seguro a  *\<aplicación >. exe.config*y el acceso de lectura y escritura seguro a *user.config*.  
  
 En una aplicación ClickOnce, el tamaño de los archivos de configuración utilizado por la configuración de la aplicación está restringido por el tamaño de la caché de ClickOnce. Para obtener más información, consulte [información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Actualizaciones de versión  
 Igual que todas las versiones de una aplicación ClickOnce está aislada de todas las demás versiones, la configuración de la aplicación para una aplicación ClickOnce está aislada de la configuración de otras versiones también. Cuando el usuario realiza una actualización a una versión posterior de la aplicación, configuración de la aplicación compara configuración más reciente (con el número mayor) de la versión con los ajustes proporcionados con la versión actualizada y combina la configuración en un nuevo conjunto de archivos de configuración.  
  
 En la tabla siguiente se describe cómo la configuración de la aplicación decide qué opciones de configuración para copiar.  
  
|Tipo de cambio|Acción de actualización|  
|--------------------|--------------------|  
|Se agregó a la configuración  *\<aplicación >. exe.config*|La nueva configuración se combina con la versión actual  *\<aplicación >. exe.config*|  
|Configuración quitó  *\<aplicación >. exe.config*|La configuración antigua se quita de la versión actual  *\<aplicación >. exe.config*|  
|Valor predeterminado de la configuración ha cambiado; configuración local sigue establecida en original predeterminada en *user.config*|La configuración se combina con la versión actual *user.config* con el nuevo valor predeterminado como el valor|  
|Valor predeterminado de la configuración ha cambiado; conjunto de configuración no predeterminados en *user.config*|La configuración se combina con la versión actual *user.config* con el valor no predeterminado que se conservan|  
  
Si ha creado su propia configuración de la aplicación de clase de contenedor y desea personalizar la lógica de actualización, puede invalidar el \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > método.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce y configuración de roaming  
 ClickOnce no funciona con la configuración de roaming, que permite que el archivo de configuración para siga todas las máquinas en una red. Si necesita la configuración de roaming, necesita implementar un proveedor de configuración de aplicación que almacena la configuración a través de la red, o desarrollar sus propias clases de configuración personalizada para almacenar la configuración en un equipo remoto. Para obtener más información en los proveedores de configuración, consulte [arquitectura de configuración de aplicación](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Introducción a la configuración de la aplicación](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
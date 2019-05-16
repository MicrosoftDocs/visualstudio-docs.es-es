---
title: ClickOnce y configuración de la aplicación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696689"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce y configuración de la aplicación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Configuración de la aplicación para Windows Forms facilita crear, almacenar y mantener aplicaciones personalizadas y las preferencias del usuario en el cliente. El siguiente documento describe cómo funcionan los archivos de configuración de aplicación en una aplicación ClickOnce y cómo ClickOnce migra la configuración cuando el usuario realiza una actualización a la siguiente versión.  
  
 La siguiente información se aplica solo para el proveedor de configuración de aplicación predeterminado, el <xref:System.Configuration.LocalFileSettingsProvider> clase. Si se proporciona un proveedor personalizado, ese proveedor determinará cómo almacena sus datos y cómo actualiza la configuración entre versiones. Para obtener más información sobre los proveedores de configuración de aplicación, consulte [Application Settings Architecture](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Archivos de configuración de la aplicación  
 Configuración de la aplicación consume los dos archivos: *aplicación*. exe.config y user.config, donde *aplicación* es el nombre de la aplicación de Windows Forms. el archivo User.config se crea en el cliente la primera vez que la aplicación almacena la configuración de ámbito de usuario. *aplicación*. exe.config, por el contrario, existirá antes de la implementación si define los valores predeterminados para la configuración. Visual Studio incluirá este archivo automáticamente cuando se usa su **publicar** comando. Si crea su aplicación ClickOnce mediante Mage.exe o MageUI.exe, debe asegurarse de que este archivo se incluye con la aplicación de otros archivos al rellenar el manifiesto de aplicación.  
  
 En aplicaciones no implementadas con ClickOnce, una aplicación Windows Forms *aplicación*. archivo exe.config se almacena en el directorio de la aplicación, mientras que el archivo user.config se almacena en el usuario **Documents and Settings**  carpeta. En una aplicación ClickOnce, *aplicación*. exe.config se encuentra en el directorio de la aplicación dentro de la caché de la aplicación ClickOnce y user.config reside en el directorio de datos de ClickOnce para esa aplicación.  
  
 Independientemente de cómo implementar la aplicación, configuración de la aplicación garantiza el acceso de lectura seguro a *aplicación*. exe.config y acceso de lectura y escritura seguro a user.config.  
  
 En una aplicación ClickOnce, el tamaño de los archivos de configuración utilizado por la configuración de la aplicación está restringido por el tamaño de la caché de ClickOnce. Para obtener más información, consulte [información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Actualizaciones de versión  
 Igual que todas las versiones de una aplicación ClickOnce está aislada de todas las demás versiones, la configuración de la aplicación para una aplicación ClickOnce está aislada de la configuración de otras versiones también. Cuando el usuario realiza una actualización a una versión posterior de la aplicación, configuración de la aplicación compara configuración más reciente (con el número mayor) de la versión con los ajustes proporcionados con la versión actualizada y combina la configuración en un nuevo conjunto de archivos de configuración.  
  
 En la tabla siguiente se describe cómo la configuración de la aplicación decide qué opciones de configuración para copiar.  
  
|Tipo de cambio|Acción de actualización|  
|--------------------|--------------------|  
|Se agregó a la configuración *aplicación*. exe.config|La nueva configuración se combina con la versión actual *aplicación*. exe.config|  
|Configuración quitó *aplicación*. exe.config|La configuración antigua se quita de la versión actual *aplicación*. exe.config|  
|Valor predeterminado de la configuración ha cambiado; configuración local sigue establecida en predeterminado original en el archivo user.config|La configuración se combina en el archivo user.config de la versión actual con el nuevo valor predeterminado como el valor|  
|Valor predeterminado de la configuración ha cambiado; configuración establecida en no predeterminado en el archivo user.config|La configuración se combina en el archivo user.config de la versión actual con el valor no predeterminado que se conservan|  
  
 Si ha creado su propia configuración de la aplicación de clase de contenedor y desea personalizar la lógica de actualización, puede invalidar el <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> método.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce y configuración de Roaming  
 ClickOnce no funciona con la configuración de roaming, que permite que el archivo de configuración para siga todas las máquinas en una red. Si necesita la configuración de roaming, necesita implementar un proveedor de configuración de aplicación que almacena la configuración a través de la red, o desarrollar sus propias clases de configuración personalizada para almacenar la configuración en un equipo remoto. Para obtener más información en los proveedores de configuración, consulte [Application Settings Architecture](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Introducción a la configuración de la aplicación](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [ClickOnce Cache Overview](../deployment/clickonce-cache-overview.md)   
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)

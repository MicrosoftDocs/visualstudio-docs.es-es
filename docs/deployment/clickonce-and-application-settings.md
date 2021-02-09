---
title: ClickOnce y configuración de la aplicación | Microsoft Docs
description: Obtenga información sobre cómo funcionan los archivos de configuración de la aplicación en una aplicación ClickOnce y cómo ClickOnce migra la configuración cuando el usuario realiza la actualización a la versión siguiente.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96491dc192b6578abd725d5d69b7c9093e92b20c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896395"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce y configuración de la aplicación
La configuración de la aplicación para Windows Forms facilita la creación, el almacenamiento y el mantenimiento de las preferencias de usuario y aplicación personalizadas en el cliente. En el documento siguiente se describe cómo funcionan los archivos de configuración de la aplicación en una aplicación ClickOnce y cómo ClickOnce migra la configuración cuando el usuario se actualiza a la versión siguiente.

 La información siguiente solo se aplica al proveedor de configuración de la aplicación predeterminado, la <xref:System.Configuration.LocalFileSettingsProvider> clase. Si proporciona un proveedor personalizado, ese proveedor determinará cómo almacena sus datos y cómo actualiza su configuración entre versiones. Para obtener más información sobre los proveedores de configuración de la aplicación, consulte [arquitectura de configuración](/dotnet/framework/winforms/advanced/application-settings-architecture)de la aplicación.

## <a name="application-settings-files"></a>Archivos de configuración de la aplicación
 La configuración de la aplicación consume dos archivos: *\<app>.exe.config* y *user.config*, donde *App* es el nombre de la aplicación Windows Forms. *user.config* se crea en el cliente la primera vez que la aplicación almacena la configuración de ámbito de usuario. Por el contrario, *\<app>.exe.config* existirá antes de la implementación si se definen los valores predeterminados para la configuración. Visual Studio incluirá este archivo automáticamente al usar el comando **publicar** . Si crea su aplicación ClickOnce con *Mage.exe* o *MageUI.exe*, debe asegurarse de que este archivo está incluido en los otros archivos de la aplicación al rellenar el manifiesto de aplicación.

 En una aplicación Windows Forms no implementada mediante ClickOnce, el archivo de *\<app>.exe.config* de una aplicación se almacena en el directorio de la aplicación, mientras que el archivo *user.config* se almacena en la carpeta **Documents and Settings** del usuario. En una aplicación ClickOnce, *\<app>.exe.config* reside en el directorio de la aplicación dentro de la memoria caché de la aplicación ClickOnce y *user.config* reside en el directorio de datos de ClickOnce para esa aplicación.

 Independientemente de cómo implemente su aplicación, la configuración de la aplicación garantiza un acceso de lectura seguro a *\<app>.exe.config* y acceso de lectura/escritura seguro a *user.config*.

 En una aplicación ClickOnce, el tamaño de los archivos de configuración que usa la configuración de la aplicación está restringido por el tamaño de la caché de ClickOnce. Para obtener más información, vea [información general sobre la caché ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Actualizaciones de versiones
 Del mismo modo que cada versión de una aplicación ClickOnce está aislada de todas las demás versiones, la configuración de la aplicación para una aplicación ClickOnce se aísla también de la configuración de otras versiones. Cuando el usuario se actualiza a una versión posterior de la aplicación, la configuración de la aplicación compara la configuración de la versión más reciente (con el número más alto) con la configuración proporcionada con la versión actualizada y combina la configuración en un nuevo conjunto de archivos de configuración.

 En la tabla siguiente se describe cómo la configuración de la aplicación decide qué configuración se va a copiar.

|Tipo de cambio|Acción de actualización|
|--------------------|--------------------|
|Configuración agregada a *\<app>.exe.config*|La nueva configuración se combina en la *\<app>.exe.config* de la versión actual|
|Configuración quitada de *\<app>.exe.config*|La configuración anterior se quita del *\<app>.exe.config* de la versión actual|
|Se ha cambiado el valor predeterminado de la configuración; la configuración local todavía está establecida en el valor predeterminado original en *user.config*|La configuración se combina en el *user.config* de la versión actual con el nuevo valor predeterminado como el valor.|
|Se ha cambiado el valor predeterminado de la configuración; establecer en no predeterminado en *user.config*|La configuración se combina en la *user.config* de la versión actual con el valor no predeterminado conservado|

Si ha creado su propia clase contenedora de configuración de la aplicación y desea personalizar la lógica de actualización, puede invalidar el <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> método.

## <a name="clickonce-and-roaming-settings"></a>Configuración de ClickOnce y roaming
 ClickOnce no funciona con la configuración de itinerancia, lo que permite que el archivo de configuración le siga entre los equipos de una red. Si necesita una configuración de itinerancia, debe implementar un proveedor de configuración de la aplicación que almacene la configuración a través de la red, o bien desarrollar sus propias clases de configuración personalizadas para almacenar la configuración en un equipo remoto. Para obtener más información sobre los proveedores de configuración, consulte [arquitectura de configuración](/dotnet/framework/winforms/advanced/application-settings-architecture)de la aplicación.

## <a name="see-also"></a>Vea también
- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Información general de configuración de la aplicación](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md)
- [Acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
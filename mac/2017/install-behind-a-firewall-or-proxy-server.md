---
title: Instalación y uso de Visual Studio para Mac detrás de un firewall o servidor proxy
description: En este documento se proporciona una lista de hosts que deben estar en la lista blanca del firewall para permitir que Visual Studio para Mac (y sus cargas de trabajo, incluido Xamarin) trabaje en un entorno corporativo.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: asb3993
ms.author: amburns
ms.date: 10/23/2018
ms.openlocfilehash: 70ac8defdcea9cccd8a3b3f9be71d38fb78c9c50
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568347"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalación y uso de Visual Studio para Mac detrás de un firewall o servidor proxy

Si usted o su organización utiliza medidas de seguridad como un firewall o un servidor proxy, hay direcciones URL de dominio que quizá desee "incluir en una lista de permitidos", así como puertos y protocolos que desea abrir para tener la mejor experiencia al instalar y utilizar Visual Studio para Mac y los servicios de Azure.

- [**Instalación de Visual Studio para Mac**](#install-visual-studio-for-mac): Estas tablas incluyen las direcciones URL en la lista blanca para que tenga acceso a todas las características y cargas de trabajo de Visual Studio para Mac.

- [**Uso de Visual Studio para Mac**](#use-visual-studio-for-mac): Estas tablas incluyen las direcciones URL en la lista blanca para que tenga acceso a todos los servicios y las características que quiera.

## <a name="install-visual-studio-for-mac"></a>Instalación de Visual Studio para Mac

Como el instalador de Visual Studio para Mac descarga de varios dominios y servidores de descarga, estos son los dominios y las direcciones URL que quizás quera agregar como de confianza en sus configuraciones.

### <a name="microsoft-domains"></a>Dominios de Microsoft

| Dominio| Propósito |
| ----------------------------------- |---------------------------|
| *.live.com| Administración de credenciales |
| app.vssps.visualstudio.com| Metadatos de instalador|
| vortex.data.microsoft.com | Informes de bloqueo y errores |
| az667904.vo.msecnd.net| Informes de bloqueo y errores |
| xamarin.com | Metadatos de instalador|
| xampubdl.blob.core.windows.net| Paquetes de instalador|
| download.visualstudio.microsoft.com | Paquetes de instalador|
| xamarin.azureedge.net | Paquetes de instalador|
| developer.xamarin.com | Paquetes de instalador|
| dc.services.visualstudio.com| Informe de bloqueos |

### <a name="third-party-domains"></a>Dominios de terceros

| Dominio| Propósito |
| --------------------------|-------------------------|
| dl.google.com | SDK de Android |
| download.oracle.com | SDK de Java|
| api.apple-cloudkit.com| Servicios de seguridad de Azure |

## <a name="use-visual-studio-for-mac"></a>Uso de Visual Studio para Mac

Para asegurarse de que tiene acceso a cada característica que necesita en Visual Studio para Mac al estar detrás de un proxy o firewall, le recomendamos agregar a la lista blanca los siguientes dominios y puertos.

### <a name="general"></a>General

| Dominio | Puertos|Propósito|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Resolución de direcciones URL de Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Datos de la página de inicio|
| software.xamarin.com |  80/443|Servicio de actualización|
| addins.monodevelop.com | 80/443| Servicios de extensión |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Notificaciones y característica experimental |
| targetednotifications.azurewebsites.net|  80/443| Se utiliza para filtrar una lista global de notificaciones a una lista que solo se aplica a tipos específicos de máquinas/escenarios de uso.|

### <a name="identity"></a>identidad

| Dominio | Puertos|Propósito|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Proveedor de identidades|
| secure.aadcdn.microsoftonline-p.com | 80/443|Proveedor de identidades|
| dc.services.visualstudio.com| 80/443|Informe de bloqueos|
| management.azure.com|80/443| API Servicios de Azure |

### <a name="nuget"></a>NuGet

| Dominio | Puertos|Propósito|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|API NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Proveedor de identidades|

### <a name="android-projects"></a>Proyectos de Android

| Dominio| Propósito|
| ------------------------------------|------------------------------------|
| time.android.com| Servidor horario para Android Emulator |
| connectivitycheck.gstatic.com | Conectividad para Android Emulator|
| cloudconfig.googleapis.com| API para Android Emulator|

## <a name="see-also"></a>Vea también

- [Instalación y uso de Visual Studio 2017 y de servicios de Azure detrás de un firewall o servidor proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)

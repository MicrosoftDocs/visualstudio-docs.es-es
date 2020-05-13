---
title: Instalación y uso de Visual Studio para Mac detrás de un firewall o servidor proxy
description: En este documento se proporciona una lista de hosts que deben estar permitidos en el firewall para que Visual Studio para Mac (y sus cargas de trabajo, incluido Xamarin) trabaje en un entorno corporativo.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 717eb9cd58f213c3d2c31a18c546a83ab8feb645
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984030"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalación y uso de Visual Studio para Mac detrás de un firewall o servidor proxy

Si usted o la organización usa medidas de seguridad como un firewall o un servidor proxy, hay dominios que quizá quiera agregar a una "lista de permitidas", así como puertos y protocolos que quiera abrir para tener la mejor experiencia posible a la hora de instalar y usar Visual Studio para Mac y los servicios de Azure.

- [**Instalación de Visual Studio para Mac**](#install-visual-studio-for-mac): Estas tablas incluyen los dominios que deben permitir la conectividad para que tenga acceso a todas las características y cargas de trabajo de Visual Studio para Mac.

- [**Uso de Visual Studio para Mac**](#use-visual-studio-for-mac): Estas tablas indican los dominios que deben permitir la conectividad para que tenga acceso a las características relacionadas.

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
| static.xamarin.com | Paquetes de instalador|
| dl.xamarin.com | Paquetes de instalador|
| dc.services.visualstudio.com| Informe de bloqueos |

### <a name="third-party-domains"></a>Dominios de terceros

| Dominio| Propósito |
| --------------------------|-------------------------|
| dl.google.com | SDK de Android |
| download.oracle.com | SDK de Java|
| api.apple-cloudkit.com| Servicios de seguridad de Azure |

## <a name="use-visual-studio-for-mac"></a>Uso de Visual Studio para Mac

Para asegurarse de que tiene acceso a cada característica que necesita en Visual Studio para Mac al estar detrás de un proxy o firewall, le recomendamos agregar a la lista de acceso permitido los siguientes dominios y puertos.

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

- [Instalación y uso de Visual Studio y de servicios de Azure detrás de un firewall o servidor proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)

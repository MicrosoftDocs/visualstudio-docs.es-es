---
title: "Instalar Visual Studio detrás de un firewall o servidor proxy | Documentos de Microsoft"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 1e017806ca7bf3d23410ba3a2f999dca0b78f240
ms.openlocfilehash: cb2ef641cb5b9b6efbd1aeb539154da1e4082b51
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Instalar Visual Studio detrás de un firewall o servidor proxy

El Instalador de Visual Studio descarga archivos de distintos dominios y sus servidores de descarga. Esta página enumera las direcciones URL de dominio que le recomendamos que agregue a la "lista blanca" como de confianza en los scripts de implementación.

Si es posible para su entorno, considere la posibilidad de agregar los dominios siguientes con protocolos HTTP y HTTPS.

## <a name="microsoft-domains"></a>Dominios de Microsoft
| Dominio | Finalidad |
| ------ | ------- |
| go.microsoft.com | Configurar URL de resolución |
| aka.ms | Configurar URL de resolución |
| download.visualstudio.microsoft.com | Configurar ubicación de descarga de los paquetes |
| download.microsoft.com | Configurar ubicación de descarga de los paquetes |
| download.visualstudio.com | Configurar ubicación de descarga de los paquetes |
| dl.xamarin.com | Configurar ubicación de descarga de los paquetes |
| visualstudiogallery.msdn.microsoft.com | Ubicación de descarga de las extensiones de Visual Studio |
| www.visualstudio.com | Ubicación de la documentación |
| docs.microsoft.com | Ubicación de la documentación |
| msdn.microsoft.com | Ubicación de la documentación |
| www.microsoft.com | Ubicación de la documentación |
| *.windows.net | Ubicación de inicio de sesión |
| *.microsoftonline.com | Ubicación de inicio de sesión |
| *.live.com | Ubicación de inicio de sesión |


## <a name="non-microsoft-domains"></a>Dominios que no son de Microsoft
| Dominio | Instala estas cargas de trabajo. |
| ------ | ------- |
| archive.apache.org |  Desarrollo móvil con JavaScript <br />(Cordova) |
| cocos2d-x.org | Desarrollo de juegos con C++ <br />(Cocos) |
| download.epicgames.com | Desarrollo de juegos con C++ <br />(Unreal Engine) |
| download.oracle.com | Desarrollo móvil con JavaScript <br />(SDK de Java) <br /><br />Desarrollo móvil con .NET <br />(SDK de Java) |
| download.unity3d.com | Desarrollo de juegos con Unity <br />(Unity) |
| netstorage.unity3d.com | Desarrollo de juegos con Unity <br /> (Unity) |
| dl.google.com | Desarrollo móvil con JavaScript <br />(Android SDK y NDK, emulador) <br /><br />Desarrollo móvil con .NET <br />(Android SDK y NDK, emulador) |
| www.incredibuild.com | Desarrollo de juegos con C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Desarrollo de juegos con C++ <br />(IncrediBuild) |
| www.python.org | Desarrollo de Python <br />(Python) <br /><br />Aplicaciones analíticas y de ciencia de datos <br />(Python) |

## <a name="see-also"></a>Vea también
* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
  * [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
    * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
    * [Carga de trabajo y referencia de id. de componente](workload-and-component-ids.md)
  * [Crear una instalación basada en red de Visual Studio](create-a-network-installation-of-visual-studio.md)
    * [Consideraciones especiales para instalar Visual Studio en un entorno sin conexión](install-visual-studio-in-offline-environment.md)
  * [Automatizar Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md)
  * [Aplicar automáticamente las claves de producto durante la implementación de Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [Establecer valores predeterminados para implementaciones empresariales de Visual Studio](set-defaults-for-enterprise-deployments.md)
  * [Deshabilitar o mover la caché del paquete](disable-or-move-the-package-cache.md)
  * [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
  * [Controlar las actualizaciones a implementaciones de Visual Studio](controlling-updates-to-visual-studio-deployments.md)
  * [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
  * [Notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)


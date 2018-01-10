---
title: "Instalar Visual Studio detrás de un firewall o servidor proxy | Documentos de Microsoft"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
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
ms.workload: multiple
ms.openlocfilehash: 3862c6ed49e00ffa3800cccbedb2b846823418ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Instalar Visual Studio detrás de un firewall o servidor proxy

El Instalador de Visual Studio descarga archivos de distintos dominios y sus servidores de descarga. Esta página enumera las direcciones URL de dominio que le recomendamos que agregue a la "lista blanca" como de confianza en los scripts de implementación.

Si es posible para su entorno, considere la posibilidad de agregar los dominios siguientes con protocolos HTTP y HTTPS.

## <a name="microsoft-domains"></a>Dominios de Microsoft
| Dominio | Propósito |
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

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también
* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
  * [Carga de trabajo y referencia de id. de componente](workload-and-component-ids.md)
* [Crear una instalación basada en red de Visual Studio 2017](create-a-network-installation-of-visual-studio.md)
  * [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatizar la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md)
* [Aplicar automáticamente las claves de producto durante la implementación de Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Establecer valores predeterminados para implementaciones empresariales de Visual Studio 2017](set-defaults-for-enterprise-deployments.md)
* [Deshabilitar o mover la caché del paquete](disable-or-move-the-package-cache.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Controlar las actualizaciones de implementaciones de Visual Studio 2017](controlling-updates-to-visual-studio-deployments.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)

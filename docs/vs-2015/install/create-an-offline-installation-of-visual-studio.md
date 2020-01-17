---
title: Creación de una instalación sin conexión | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 72bf11519ec500082304fde431122d05ee65db54
ms.sourcegitcommit: 3b48ce4649d38a7e3b095bd087739d6131e49d1b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76124522"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Crear una instalación sin conexión de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [Crear una instalación sin conexión de Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) o [Creación de una instalación de red de Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Esta página describe cómo instalar Visual Studio 2015 cuando no está conectado a Internet. Sin embargo, para llevar a cabo una instalación "desconectada", primero debe crear un diseño de instalación sin conexión mediante el uso de una máquina que esté conectada a Internet. A continuación le mostramos cómo hacerlo.

> [!IMPORTANT]
> Si el equipo sin conexión está ejecutando Windows 7 SP1 o Windows Server 2008 R2, consulte las instrucciones especiales en la sección [Solución de problemas de una instalación sin conexión](#BKMK_tshoot) de este tema.  Debe seguir estas instrucciones *antes* de instalar Visual Studio 2015.

## <a name="BKMK_Offline"></a> Instalación mediante la creación de una instalación sin conexión

#### <a name="to-create-an-offline-installation-layout"></a>Para crear un diseño de instalación sin conexión

1. Elija la edición de Visual Studio que desea instalar desde la página de descarga [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015).

2. Después de descargar el instalador en una ubicación del sistema de archivos, ejecute "\<nombre del archivo ejecutable >/layout".

     Por ejemplo, ejecute: `vs_enterprise.exe /layout D:\VisualStudio2015`.

     Con el conmutador `/layout`, puede descargar casi todos los paquetes de instalación, no solo los que se aplican a la máquina de descarga. Este enfoque le proporciona los archivos que necesita para ejecutar este programa de instalación en cualquier parte y puede resultar útil si desea instalar componentes que no se instalaron originalmente.

3. Después de ejecutar este comando, aparecerá un cuadro de diálogo que le permite cambiar la carpeta donde desea que resida el diseño de instalación sin conexión.   Luego, haga clic en el botón **Descargar**.

     Cuando la descarga del paquete haya finalizado, debería ver el mensaje **¡La instalación se realizó correctamente! Todos los componentes especificados se han adquirido correctamente.**

4. Busque la carpeta que especificó anteriormente. (Por ejemplo, D:\VisualStudio2015). Esta carpeta contiene todo lo que necesita copiar en una ubicación compartida o en discos de instalación.

    > [!CAUTION]
    > Actualmente, el SDK de Android no admite una experiencia de instalación sin conexión. Si instala elementos de la instalación del SDK de Android en un equipo que no está conectado a Internet, es posible que se produzca un error en la instalación. Para obtener más información, vaya a la sección "Solucionar los problemas de una instalación sin conexión" de este tema.

5. Ejecute la instalación desde la ubicación del archivo o desde los discos de instalación.

## <a name="updating-an-offline-installation"></a>Actualización de una instalación sin conexión
 Microsoft ha publicado varias actualizaciones para Visual Studio 2015. Para actualizar la instalación de Visual Studio, simplemente descargue la edición que desee desde la página de descarga [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015). A continuación, siga los pasos descritos en este tema para crear un nuevo diseño de instalación sin conexión y, a continuación, úselo para actualizar su copia de Visual Studio 2015.

## <a name="BKMK_tshoot"></a> Solución de problemas de una instalación sin conexión
 Al instalar sin conexión desde la caché de instalación sin conexión, es posible que aparezcan mensajes de advertencia sobre la imposibilidad de instalar algunos componentes y paquetes. En la siguiente tabla se incluyen posibles soluciones para estos escenarios.

| Componente o paquete | Soluciones |
|-|-|
| Dotfuscator y Analytics Community Edition 5.19.1 (para las ediciones Community, Professional y Enterprise de Visual Studio, tal y como se instala en **Windows 7 SP1** y **Windows Server 2008 R2**) | Si la máquina sin conexión ejecuta **Windows 7 SP1** o **Windows Server 2008 R2**, debe realizar los pasos siguientes antes de instalar Visual Studio 2015:<br /><br /> 1.  Configure un archivo o servidor web para descargar los archivos CTL.<br /><br /> 2.    Redirija la dirección URL de actualización automática de Microsoft para un entorno desconectado.<br /><br /> Para obtener más información, consulte la página [Configure Trusted Roots and Disallowed Certificates](https://technet.microsoft.com/library/dn265983.aspx) (Configuración de raíces de confianza y certificados no permitidos) en el sitio de Microsoft TechNet. |
| Programa de instalación de Android SDK (nivel de API) | Debe tener una conexión a Internet para instalar paquetes de Android SDK (nivel de API). Si está en una red restringida, debe permitir el acceso a las siguientes direcciones URL cuando instale Visual Studio:<br /><br /> -   https://dl.google.com:443<br />-   https://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Para obtener información sobre cómo resolver posibles problemas con la configuración de proxy, vea la publicación del blog [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errores de instalación de Visual Studio 2015 [Instalación de Android SDK] detrás de un proxy). |
| Plantillas de elemento de extensibilidad de Visual Studio<br /><br /> Extensión de GitHub para Visual Studio<br /><br /> Herramientas de PowerShell para Visual Studio | Si no tiene conexión a Internet al instalar Visual Studio 2015, puede utilizar una fuente sin conexión especial para generar el diseño de instalación sin conexión. **Nota:**  Esta fuente especial incluye las actualizaciones más recientes para Visual Studio 2015. <br /><br /> Para crear la fuente sin conexión especial, ejecute el comando siguiente: /layout *Unidad:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*<br /><br /> Por ejemplo, para una fuente sin conexión especial en inglés de Visual Studio 2015 Enterprise, ejecute:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Para obtener una lista completa de las direcciones URL que puede usar para crear una fuente sin conexión especial en el idioma que prefiera, vea la tabla siguiente. |

 Use las direcciones URL siguientes para crear una fuente sin conexión especial específica de un idioma, como se describe en la tabla anterior.

|       Lenguaje        |                            Resolución                            |
|-----------------------|-----------------------------------------------------------|
| Chino (simplificado)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chino (tradicional) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Checo         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Alemán         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Inglés        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Español        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francés         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italiano        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonés        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Coreano         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polaco         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugués       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Ruso        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turco        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Vea también

- [Instalar Visual Studio](install-visual-studio-2015.md)
---
title: Crear una instalación sin conexión | Microsoft Docs
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
ms.openlocfilehash: 8d76e4b1c9a7f7b6882eccab4a250e95c7419ea0
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763138"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Crear una instalación sin conexión de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [instalar Visual Studio 2017 en entornos de red poco confiables o de bajo ancho de banda](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), o [crear una instalación de red de Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) y [Consideraciones especiales para instalar Visual Studio 2017 en un entorno sin conexión](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Esta página describe cómo instalar Visual Studio 2015 cuando no están conectados a Internet. Sin embargo, para llevar a cabo una instalación "desconectada", primero debe crear un diseño de instalación sin conexión mediante el uso de una máquina que está conectada a Internet. A continuación le mostramos cómo hacerlo.

> [!IMPORTANT]
>  Si el equipo sin conexión se está ejecutando Windows 7 SP1 o Windows Server 2008 R2, consulte las instrucciones especiales en el [solución de problemas de una instalación sin conexión](#BKMK_tshoot) sección de este tema.  Debe seguir estas instrucciones *antes* instalar Visual Studio 2015.

##  <a name="BKMK_Offline"></a> Instalación mediante la creación de una instalación sin conexión

#### <a name="to-create-an-offline-installation-layout"></a>Para crear un diseño de instalación sin conexión

1.  Elija la edición de Visual Studio que desea instalar desde el [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) página de descarga.

2.  Después de descargar el instalador en una ubicación en el sistema de archivos, ejecute "\<nombre del archivo ejecutable >/Layout".

     Por ejemplo, ejecute: `vs_enterprise.exe /layout D:\VisualStudio2015`.

     Mediante el uso de la `/layout` conmutador, puede descargar casi todos los paquetes de instalación, no solo los que se aplican al equipo de descarga. Este enfoque le proporciona los archivos que necesita para ejecutar a este instalador en cualquier lugar y puede ser útil si desea instalar los componentes que no se instalaron originalmente.

3.  Después de ejecutar este comando, aparecerá un cuadro de diálogo que le permite cambiar la carpeta donde desea que resida el diseño de instalación sin conexión.   A continuación, haga clic en el **descargar** botón.

     Cuando la descarga del paquete se realiza correctamente, debería ver un mensaje que dice **instalación se realizó correctamente! Todos los componentes especificados se han adquirido correctamente.**

4.  Busque la carpeta que especificó anteriormente. (Por ejemplo, busque D:\VisualStudio2015). Esta carpeta contiene todo lo que necesita para copiar en una ubicación compartida o medios de instalación.

    > [!CAUTION]
    >  Actualmente, el SDK de Android no admite una experiencia de instalación sin conexión. Si instala elementos de la instalación del SDK de Android en un equipo que no está conectado a Internet, es posible que se produzca un error en la instalación. Para obtener más información, consulte la sección "Solución de problemas de una instalación sin conexión" en este tema.

5.  Ejecute la instalación desde la ubicación del archivo o desde el medio de instalación.

## <a name="updating-an-offline-installation"></a>Actualizar una instalación sin conexión
 Microsoft ha lanzado varias actualizaciones para Visual Studio 2015. Para actualizar la instalación de Visual Studio, simplemente descargue la edición que desee desde la de la [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) página de descarga. A continuación, siga los pasos descritos en este tema para crear un nuevo diseño de instalación sin conexión y, a continuación, usarla para actualizar su copia de Visual Studio 2015.

##  <a name="BKMK_tshoot"></a> Solución de problemas de una instalación sin conexión
 Al instalar sin conexión desde la caché de instalación sin conexión, es posible que aparezcan mensajes de advertencia sobre la imposibilidad de instalar algunos componentes y paquetes. En la siguiente tabla se incluyen posibles soluciones para estos escenarios.


|                                                                                       Componente o paquete                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   Soluciones                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dotfuscator y Analytics Community Edition 5.19.1 (para las ediciones Community, Professional y Enterprise de Visual Studio, tal y como se instala en **Windows 7 SP1** y **Windows Server 2008 R2**) |                                                                                                                                       Si se está ejecutando la máquina sin conexión **Windows 7 SP1** o **Windows Server 2008 R2**, debe realizar los pasos siguientes antes de instalar Visual Studio 2015:<br /><br /> 1.  Configurar un servidor web o de archivos para descargar los archivos CTL.<br /><br /> 2.    Redirigir the Microsoft Automatic Update URL para un entorno desconectado.<br /><br /> Para obtener más información, consulte el [configurar raíces de confianza y certificados no permitidos](https://technet.microsoft.com/library/dn265983.aspx) página en el sitio de Microsoft TechNet.                                                                                                                                       |
|                                                                                  Programa de instalación de Android SDK (nivel de API)                                                                                   |                                                                        Debe tener una conexión a Internet para instalar paquetes de Android SDK (nivel de API). Si está en una red restringida, debe permitir el acceso a las siguientes direcciones URL cuando instale Visual Studio:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Para obtener información sobre cómo resolver posibles problemas con la configuración de proxy, vea la publicación del blog [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errores de instalación de Visual Studio 2015 [Instalación de Android SDK] detrás de un proxy).                                                                         |
|                             Plantillas de elemento de extensibilidad de Visual Studio<br /><br /> Extensión de GitHub para Visual Studio<br /><br /> Herramientas de PowerShell para Visual Studio                             | Si no tiene una conexión a internet al instalar Visual Studio 2015, se puede utilizar una fuente sin conexión para generar el diseño de instalación sin conexión. **Nota:** esta fuente especial incluye las actualizaciones más recientes para Visual Studio 2015. <br /><br /> Para crear especial fuente sin conexión, ejecute el comando siguiente: / Layout *unidad:* \VisualStudio2015 /overridefeeduri *dirección URL a fuente xml*<br /><br /> Por ejemplo, para un idioma de inglés especial fuente sin conexión de Visual Studio 2015 Enterprise, ejecute:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Para obtener una lista completa de las direcciones URL que puede usar para crear un especial fuente sin conexión en el lenguaje de su elección, vea la tabla siguiente. |

 Use las direcciones URL siguientes para crear una fuente sin conexión de específico del lenguaje especial, como se describe en la tabla anterior.


|       Lenguaje        |                            Resolución                            |
|-----------------------|-----------------------------------------------------------|
| Chino (simplificado)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chino (tradicional) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Checo         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Alemán         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Inglés        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Español        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francés         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italiano        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonés        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Coreano         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polaco         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugués       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Ruso        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turco        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Vea también
 [Instalar Visual Studio]()
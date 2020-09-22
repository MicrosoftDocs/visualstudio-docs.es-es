---
title: 'Procedimiento: Instalación de una versión específica | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842923"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Cómo: Instalar una versión específica de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Actualizamos el programa de instalación de Visual Studio a menudo para que obtenga la versión más reciente y optimizada de nuestras características opcionales.  Sin embargo, si quiere instalar una versión anterior de Visual Studio 2015, como, por ejemplo, una versión anterior a Visual Studio 2015 Update 1 con compatibilidad con iOS, deberá forzar que el programa de instalación de Visual Studio use una versión anterior de los archivos de manifiesto de características. En este artículo se describe cómo hacerlo.

## <a name="installing-the-current-release"></a>Instalar la versión actual
 Desde el primer lanzamiento de Visual Studio 2015, hemos actualizado el motor de instalación y los archivos de manifiesto varias veces.  Esto significa que si descarga el instalador web del sitio web [Descargas de Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) en una máquina limpia conectada a Internet, el programa de instalación instala la actualización más reciente de Visual Studio 2015, que incluye las últimas mejoras del producto, así como las versiones más nuevas y recientes de las herramientas y características opcionales.

## <a name="installing-earlier-releases"></a>Instalar versiones anteriores
 Puede crear y montar una imagen ISO, o puede descargar e iniciar el instalador directamente desde [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) y después anexar el archivo .exe con parámetros de línea de comandos adicionales (como /CustomInstallPath, /Full, /InstallSelectableItems, /NoRestart, etc.) para controlar cómo se instala Visual Studio.

 En la tabla siguiente se incluyen algunos escenarios específicos de un momento determinado en el tiempo y los parámetros de línea de comandos necesarios que debe pasar al instalador de la edición Enterprise. (Los mismos parámetros también funcionarán con los instaladores de las ediciones Community o Professional).

|Edición de Visual Studio 2015|Qué ejecutar|Línea de comandos que se va a usar|Qué hace la configuración|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (última versión pública)|Visual Studio Enterprise con actualizaciones (disponible en [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Nota:** El comportamiento predeterminado de esta instalación ofrece las últimas características opcionales y, por lo tanto, no requiere ningún parámetro de línea de comandos.|El programa de instalación de Visual Studio usa el archivo feed.xml más reciente e instala los archivos más recientes|
|Visual Studio Enterprise Update 3 (versión Update 3 original sin ninguna actualización posterior)|Visual Studio Enterprise RTM (disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que estaba disponible cuando se lanzó Update 3|
|Visual Studio Enterprise Update 2 (la versión original de Update 2, pero con actualizaciones previas a Update 3)|Visual Studio Enterprise RTM (disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que era el actual antes del lanzamiento de Update 3|
|Visual Studio Enterprise (versión de Update 2 original sin ninguna actualización posterior)|Visual Studio Enterprise RTM (disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que estaba disponible cuando se lanzó Update 2|
|Visual Studio Enterprise Update 1 (la versión original de Update 1, pero con actualizaciones que previas a Update 2)|Visual Studio Enterprise RTM (disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que era el actual antes del lanzamiento de Update 2|
|Visual Studio Enterprise Update 1 (la versión Update 1 original sin ninguna actualización posterior)|Visual Studio Enterprise RTM (disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que estaba disponible cuando se lanzó Update 1|
|Visual Studio Enterprise (RTM original, pero con actualizaciones previas a Update 1)|Visual Studio Enterprise RTM (disponible en la  [Página de descarga de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que era el actual antes del lanzamiento de Update 1|
|Visual Studio Enterprise (RTM original sin actualizaciones)|Visual Studio Enterprise RTM (disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que estaba disponible cuando se lanzó RTM|

> [!IMPORTANT]
> Dependiendo del lenguaje que quiera usar, reemplace "enu" (en inglés) por uno de los siguientes valores:
>
> - chs (para chino (simplificado))
>   - cht (para chino (tradicional))
>   - csy (para checo)
>   - deu (para alemán)
>   - esn (para español)
>   - fra (para francés)
>   - ita (para italiano)
>   - jpa (para japonés)
>   - kor (para coreano)
>   - plk (para polaco)
>   - ptb (para portugués)
>   - rus (para ruso)
>   - trk (para turco)

## <a name="see-also"></a>Consulte también
 [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)
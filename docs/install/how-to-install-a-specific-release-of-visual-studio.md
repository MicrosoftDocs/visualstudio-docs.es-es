---
title: "C&#243;mo: Instalar una versi&#243;n espec&#237;fica de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalar una versión específica, Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# C&#243;mo: Instalar una versi&#243;n espec&#237;fica de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Actualizamos el programa de instalación de Visual Studio a menudo para que obtenga la versión más reciente y optimizada de nuestras características opcionales.  Sin embargo, si quiere instalar una versión anterior de Visual Studio 2015, como, por ejemplo, una versión anterior a Visual Studio 2015 Update 1 con compatibilidad con iOS, deberá forzar que el programa de instalación de Visual Studio use una versión anterior de los archivos de manifiesto de características. En este artículo se describe cómo hacerlo.  
  
## Instalar la versión actual  
 Desde el primer lanzamiento de Visual Studio 2015, hemos actualizado el motor de instalación una vez y los archivos de manifiesto más de cinco veces.  Esto significa que si [descarga y ejecuta el programa de instalación de Visual Studio hoy](https://www.visualstudio.com/downloads/download-visual-studio-vs) en una máquina limpia y conectada a Internet, el programa de instalación instala Visual Studio 2015 Update 1, que incluye las mejoras del producto más recientes, así como las últimas versiones de las herramientas y características opcionales.  
  
## Instalar versiones anteriores  
 Puede crear y montar una imagen ISO, o puede descargar e iniciar el instalador web directamente y después anexar el archivo .exe con parámetros de línea de comandos adicionales \(como \/CustomInstallPath, \/Full, \/InstallSelectableItems, \/NoRestart, etc.\) para controlar cómo se instala Visual Studio.  
  
 En la tabla siguiente se incluyen algunos escenarios en un momento concreto y los parámetros de línea de comandos necesarios que debe pasar al instalador web de la edición Enterprise. \(Los mismos parámetros también funcionarán con los instaladores web de las ediciones Community o Professional\).  
  
|Edición de Visual Studio 2015|Qué ejecutar|Línea de comandos que se va a usar|Qué hace la configuración|  
|-----------------------------------|------------------|----------------------------------------|-------------------------------|  
|Visual Studio Enterprise \(última versión pública\)|Visual Studio Enterprise con Update 1 \(disponible en [VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx)\)|`vs_enterprise.exe` **Note:**  El comportamiento predeterminado de esta instalación ofrece las últimas características opcionales y, por lo tanto, no requiere ningún parámetro de línea de comandos.|El programa de instalación de Visual Studio usa el archivo feed.xml más reciente e instala los archivos más recientes|  
|Visual Studio Enterprise \(RTM original, pero con actualizaciones previas a Update 1\)|Visual Studio Enterprise RTM \(disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que era el actual antes del lanzamiento de Update 1|  
|Visual Studio Enterprise Update 1 \(la versión Update 1 original sin ninguna actualización posterior\)|Visual Studio Enterprise con Update 1 \(disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que estaba disponible en Update 1|  
|Visual Studio Enterprise \(RTM original sin actualizaciones\)|Visual Studio Enterprise RTM \(disponible en la [página de descargas de suscripciones a MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|El programa de instalación de Visual Studio usará el archivo feed.xml que estaba disponible en RTM|  
  
> [!IMPORTANT]
>  Dependiendo del lenguaje que quiera usar, reemplace "enu" \(en inglés\) por uno de los siguientes valores:  
>   
>  -   chs \(para chino \(simplificado\)\)  
> -   cht \(para chino \(tradicional\)\)  
> -   csy \(para checo\)  
> -   deu \(para alemán\)  
> -   esn \(para español\)  
> -   fra \(para francés\)  
> -   ita \(para italiano\)  
> -   jpa \(para japonés\)  
> -   kor \(para coreano\)  
> -   plk \(para polaco\)  
> -   ptb \(para portugués\)  
> -   rus \(para ruso\)  
> -   trk \(para turco\)  
  
## Vea también  
 [Instalar Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)
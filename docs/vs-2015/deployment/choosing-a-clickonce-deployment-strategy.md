---
title: Elegir una estrategia de implementación de ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cce51860b335e16fe507b20e41a5adba0b3fa278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842771"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Elegir una estrategia de implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay tres estrategias distintas para implementar una aplicación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]; la estrategia que elija depende principalmente del tipo de aplicación que vaya a implementar. Las tres estrategias de implementación son las siguientes:  
  
- Instalar desde el Web o un recurso compartido de red  
  
- Instalar desde un CD  
  
- Iniciar la aplicación desde el Web o desde un recurso compartido de red  
  
    > [!NOTE]
    > Además de seleccionar una estrategia de implementación, también seleccionará una estrategia para proporcionar actualizaciones de la aplicación. Para obtener más información, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Instalar desde el Web o un recurso compartido de red  
 Con esta estrategia, su aplicación se implementa en un servidor web o en un recurso compartido de archivos de red. Cuando un usuario final desea instalar la aplicación, hace clic en un icono de una página Web o hace doble clic en un icono del recurso compartido de archivos de red. A continuación se descarga la aplicación, se instala y se inicia en el equipo del usuario final. Se agregan elementos al menú **Inicio** y a **Agregar o quitar programas** en el **Panel de control**.  
  
 Puesto que esta estrategia depende de la conectividad de la red, funciona mejor para las aplicaciones que se implementarán en usuarios con acceso a una red de área local o a una conexión a Internet de alta velocidad.  
  
 Si implementa la aplicación del Web, puede pasar los argumentos a la aplicación cuando se activa a través de la dirección URL. Para obtener más información, vea [Cómo: recuperar información de la cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). No puede pasar argumentos a una aplicación que se activa mediante alguno de los demás métodos que se describen en este documento.  
  
 Para habilitar esta estrategia de implementación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en **Del Web** o en **Desde una ruta de acceso UNC o un recurso compartido de archivos** en la página **Instalación** del Asistente para publicación.  
  
 Ésta es la estrategia de implementación predeterminada.  
  
## <a name="install-from-a-cd"></a>Instalar desde un CD  
 Con esta estrategia, su aplicación se implementa en medios extraíbles como un CD-ROM o DVD. Como en la opción anterior, cuando el usuario elige instalar la aplicación, se instala y se inicia, y se agregan elementos al menú **Inicio** y a **Agregar o quitar programas** en el **Panel de control**.  
  
 Esta estrategia funciona mejor para aplicaciones que se implementarán a los usuarios sin la conectividad de red persistente o con conexiones con un ancho de banda reducido. Dado que la aplicación se instala desde medios extraíbles, no es necesaria ninguna conexión de red para la instalación; sin embargo, la conectividad de red todavía es necesaria para las actualizaciones de la aplicación.  
  
 Para habilitar esta estrategia de implementación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en **Desde un CD-ROM o un DVD-ROM** en la página **Instalación** del Asistente para publicación.  
  
 Para habilitar esta estrategia de implementación manualmente, cambie la etiqueta **deploymentProvider** del manifiesto de implementación. (En Visual Studio, esta propiedad se expone como **URL de instalación** en la página **Publicar** del Diseñador de proyectos. En Mage.exe es **Ubicación inicial**).  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Iniciar la aplicación desde el Web o desde un recurso compartido de red  
 Esta estrategia es parecida a la primera, excepto en que la aplicación se comporta como una aplicación web. Cuando el usuario hace clic en un vínculo de una página Web (o hace doble clic en un icono del recurso compartido de archivos), se inicia la aplicación. Cuando los usuarios cierran la aplicación, deja de estar disponible en su equipo local; no se agrega nada al menú **Inicio** ni a **Agregar o quitar programas** en el **Panel de control**.  
  
> [!NOTE]
> Técnicamente, la aplicación se descarga y se instala en una caché de aplicación en el equipo local, igual que si una aplicación Web se descargara a la caché de Web. Como con la caché de Web, los archivos se recogen de la caché de la aplicación en último término. La percepción del usuario, sin embargo, es que la aplicación se ejecuta desde el web o desde el recurso compartido de archivos  
  
 Esta estrategia resulta óptima para las aplicaciones que se utilizan con poca frecuencia; por ejemplo, una herramienta de cálculo de beneficios para los que normalmente sólo se ejecuta una vez al año.  
  
 Para habilitar esta estrategia de implementación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en **No instalar la aplicación** en la página **Instalar o ejecutar desde el Web** del Asistente para publicación.  
  
 Para habilitar esta estrategia de implementación manualmente, cambie la etiqueta **install** del manifiesto de implementación. Su valor puede ser **true** o **false**. En Mage.exe, use la opción **solo en línea** de la lista tipo de **aplicación** ).  
  
## <a name="web-browser-support"></a>Compatibilidad con exploradores web  
 Las aplicaciones orientadas a .NET Framework 3.5 pueden instalarse mediante cualquier explorador.  
  
 Las aplicaciones orientadas a .NET Framework 2.0 requieren Internet Explorer.  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad e implementación de ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)

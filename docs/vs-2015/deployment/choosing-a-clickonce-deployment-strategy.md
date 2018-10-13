---
title: Elegir una estrategia de implementación de ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 54bf4f58a4cfe8622e12b3808ea9f36c8cf1ee49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175635"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Elegir una estrategia de implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay tres estrategias distintas para implementar una aplicación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]; la estrategia que elija depende principalmente del tipo de aplicación que vaya a implementar. Las tres estrategias de implementación son las siguientes:  
  
-   Instalar desde el Web o un recurso compartido de red  
  
-   Instalar desde un CD  
  
-   Iniciar la aplicación desde el Web o desde un recurso compartido de red  
  
    > [!NOTE]
    >  Además de seleccionar una estrategia de implementación, también seleccionará una estrategia para proporcionar actualizaciones de la aplicación. Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Instalar desde el Web o un recurso compartido de red  
 Con esta estrategia, su aplicación se implementa en un servidor web o en un recurso compartido de archivos de red. Cuando un usuario final desea instalar la aplicación, hace clic en un icono de una página Web o hace doble clic en un icono del recurso compartido de archivos de red. A continuación se descarga la aplicación, se instala y se inicia en el equipo del usuario final. Los elementos se agregan a la **iniciar** menú y **agregar o quitar programas** en **Panel de Control**.  
  
 Puesto que esta estrategia depende de la conectividad de la red, funciona mejor para las aplicaciones que se implementarán en usuarios con acceso a una red de área local o a una conexión a Internet de alta velocidad.  
  
 Si implementa la aplicación del Web, puede pasar los argumentos a la aplicación cuando se activa a través de la dirección URL. Para obtener más información, consulte [Cómo: recuperar información de cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). No puede pasar argumentos a una aplicación que se activa mediante alguno de los demás métodos que se describen en este documento.  
  
 Para habilitar esta estrategia de implementación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en **desde el Web** o **recurso compartido de archivo o ruta de acceso de UNC unas** en el **cómo instalan** página del Asistente para publicación.  
  
 Ésta es la estrategia de implementación predeterminada.  
  
## <a name="install-from-a-cd"></a>Instalar desde un CD  
 Con esta estrategia, su aplicación se implementa en medios extraíbles como un CD-ROM o DVD. Igual que con la opción anterior, cuando el usuario decide instalar la aplicación, se instala y se inicia y se agregan elementos a la **iniciar** menú y **agregar o quitar programas** en **Control Panel**.  
  
 Esta estrategia funciona mejor para aplicaciones que se implementarán a los usuarios sin la conectividad de red persistente o con conexiones con un ancho de banda reducido. Dado que la aplicación se instala desde medios extraíbles, no es necesaria ninguna conexión de red para la instalación; sin embargo, la conectividad de red todavía es necesaria para las actualizaciones de la aplicación.  
  
 Para habilitar esta estrategia de implementación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en **desde un CD-ROM o DVD-ROM** en el **cómo instalan** página del Asistente para publicación.  
  
 Para habilitar esta estrategia de implementación manualmente, cambie el **deploymentProvider** etiqueta en el manifiesto de implementación. (En Visual Studio, esta propiedad se expone como **dirección URL de instalación** en el **publicar** página del Diseñador de proyectos. En Mage.exe es **iniciar ubicación**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Iniciar la aplicación desde el Web o desde un recurso compartido de red  
 Esta estrategia es parecida a la primera, excepto en que la aplicación se comporta como una aplicación web. Cuando el usuario hace clic en un vínculo de una página Web (o hace doble clic en un icono del recurso compartido de archivos), se inicia la aplicación. Cuando los usuarios cierran la aplicación, ya no está disponible en su equipo local; se agrega nada a la **iniciar** menú o **agregar o quitar programas** en **Panel de Control**.  
  
> [!NOTE]
>  Técnicamente, la aplicación se descarga y se instala en una caché de aplicación en el equipo local, igual que si una aplicación Web se descargara a la caché de Web. Como con la caché de Web, los archivos se recogen de la caché de la aplicación en último término. La percepción del usuario, sin embargo, es que la aplicación se ejecuta desde el web o desde el recurso compartido de archivos  
  
 Esta estrategia resulta óptima para las aplicaciones que se utilizan con poca frecuencia; por ejemplo, una herramienta de cálculo de beneficios para los que normalmente sólo se ejecuta una vez al año.  
  
 Para habilitar esta estrategia de implementación en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en **no instalar la aplicación** en el **instalar o ejecutar desde la Web** página del Asistente para publicación.  
  
 Para habilitar esta estrategia de implementación manualmente, cambie el **instalar** etiqueta en el manifiesto de implementación. (Su valor puede ser **true** o **false**. En Mage.exe, utilice la **sólo en línea** opción el **tipo de aplicación** lista.)  
  
## <a name="web-browser-support"></a>Compatibilidad con exploradores web  
 Las aplicaciones orientadas a .NET Framework 3.5 pueden instalarse mediante cualquier explorador.  
  
 Las aplicaciones orientadas a .NET Framework 2.0 requieren Internet Explorer.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)




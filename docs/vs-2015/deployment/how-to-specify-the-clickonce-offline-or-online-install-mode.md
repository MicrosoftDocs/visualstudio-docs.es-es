---
title: 'Cómo: especificar la sin conexión de ClickOnce o instalar el modo en línea | Microsoft Docs'
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b243811f2c6c36266443cd34e0e37ddd01390f87
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266076"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Cómo: Especificar el modo de instalación en línea y sin conexión de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `Install Mode` para un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación determina si la aplicación estará disponible en línea o sin conexión. Cuando se elige **la aplicación solo está disponible en línea**, el usuario debe tener acceso a la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ubicación (una página Web o un recurso compartido de archivos) para ejecutar la aplicación de publicación. Cuando se elige **la aplicación también está disponible sin conexión**, la aplicación agrega entradas a la **iniciar** menú y el **agregar o quitar programas** cuadro de diálogo; el usuario es puede ejecutar la aplicación cuando no están conectados.  
  
 El `Install Mode` se pueden establecer en el **publicar** página de la **Diseñador de proyectos**.  
  
 **Tenga en cuenta** el `Install Mode` también se puede establecer mediante el Asistente para publicación. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Para que una aplicación ClickOnce esté disponible solo en línea  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **instalar el modo y configuración** área, haga clic en el **la aplicación solo está disponible en línea** botón de opción.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para que una aplicación ClickOnce esté disponible en línea o sin conexión  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **instalar el modo y configuración** área, haga clic en el **la aplicación también está disponible sin conexión** botón de opción.  
  
     Cuando se instala, la aplicación agrega entradas a la **iniciar** menú y a **agregar o quitar programas** en el Panel de Control.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)




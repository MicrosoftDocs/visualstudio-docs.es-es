---
title: 'Cómo: especificar la sin conexión de ClickOnce o instalar el modo en línea | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1515d9b9b12d92f7189c1dda59659d6ea1c03d5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080178"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Cómo: especificar la sin conexión de ClickOnce o instalar el modo en línea
El `Install Mode` para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación determina si la aplicación estará disponible en línea o sin conexión. Cuando se elige **la aplicación solo está disponible en línea**, el usuario debe tener acceso a la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ubicación (una página Web o un recurso compartido de archivos) para ejecutar la aplicación de publicación. Cuando se elige **la aplicación también está disponible sin conexión**, la aplicación agrega entradas a la **iniciar** menú y el **agregar o quitar programas** cuadro de diálogo; el usuario es puede ejecutar la aplicación cuando no están conectados.  
  
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
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
---
title: 'Cómo: especificar la ClickOnce sin conexión o instalar el modo en línea | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 666273ddb251057ede1788747411111f997e5d39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Cómo: Especificar el modo de instalación en línea y sin conexión de ClickOnce
El `Install Mode` para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación determina si la aplicación estará disponible sin conexión o en línea. Cuando eliges **la aplicación solo está disponible en línea**, el usuario debe tener acceso a la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ubicación de publicación (una página Web o un recurso compartido de archivos) para ejecutar la aplicación. Cuando eliges **la aplicación también está disponible sin conexión**, la aplicación agrega entradas a la **iniciar** menú y **agregar o quitar programas** cuadro de diálogo; el usuario es se puede ejecutar la aplicación cuando no están conectados.  
  
 El `Install Mode` se pueden establecer en el **publicar** página de la **Diseñador de proyectos**.  
  
 **Tenga en cuenta** el `Install Mode` también se puede establecer utilizando el Asistente para publicación. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Para que una aplicación ClickOnce esté disponible solo en línea  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **modo de instalación y configuración de** área, haga clic en el **la aplicación solo está disponible en línea** botón de opción.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para hacer una aplicación ClickOnce esté disponible en línea o sin conexión  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **modo de instalación y configuración de** área, haga clic en el **la aplicación también está disponible sin conexión** botón de opción.  
  
     Cuando se instala, la aplicación agrega entradas a la **iniciar** menú y a **agregar o quitar programas** en el Panel de Control.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
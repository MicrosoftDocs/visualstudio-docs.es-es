---
title: "Cómo: especificar una página de publicación para una aplicación ClickOnce | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 491ef29c955c5ab06b8539ec5089f2ed32feaf36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Cómo: Especificar una página de publicación para una aplicación ClickOnce
Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, se genera una página de Web predeterminada (publish.htm) y se publica junto con la aplicación. Esta página contiene el nombre de la aplicación, un vínculo para instalar la aplicación o los requisitos previos y un vínculo a un tema de ayuda que describe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. El **página publicar** propiedad del proyecto le permite especificar un nombre para la página Web para su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
 Una vez que se ha especificado la página de publicación, la próxima vez que publique, se copiará en la ubicación de publicación; no se sobrescribirá si vuelve a publicar. Si desea personalizar la apariencia de la página, puede hacerlo sin preocuparse de perder los cambios. Para obtener más información, consulte [Cómo: personalizar la página Web predeterminada de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 El **página publicar** propiedad puede establecerse el **opciones de publicación** cuadro de diálogo, accesible desde el **publicar** panel de la **Diseñador de proyectos**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Para especificar una página Web personalizada para una aplicación ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **opciones** para abrir el **opciones de publicación** cuadro de diálogo.  
  
4.  Haga clic en **implementación**.  
  
5.  En el **opciones de publicación** diálogo cuadro, asegúrese de que el **implementación abrir la página web después de publicar** casilla está activada (debe estar activada de forma predeterminada).  
  
6.  En el **página web de implementación:** cuadro, escriba el nombre de la página Web y, a continuación, haga clic en **Aceptar**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Para impedir que la página de publicación se inicie cada vez que publique  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **opciones** para abrir el **opciones de publicación** cuadro de diálogo.  
  
4.  Haga clic en **implementación**.  
  
5.  En el **opciones de publicación** cuadro de diálogo, desactive la **implementación abrir la página web después de publicar** casilla de verificación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Cómo: personalizar la página Web predeterminada de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
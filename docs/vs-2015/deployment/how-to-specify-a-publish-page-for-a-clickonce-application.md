---
title: 'Cómo: especificar una página de publicación para una aplicación ClickOnce | Microsoft Docs'
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c10033f7e3f3a4336177c8c66721bd6b79ba4c71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196695"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Cómo: Especificar una página de publicación para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al publicar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, se genera una página de Web predeterminada (publish.htm) y se publica junto con la aplicación. Esta página contiene el nombre de la aplicación, un vínculo para instalar la aplicación o los requisitos previos y un vínculo a un tema de ayuda que describe [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. El **página publicar** propiedad del proyecto le permite especificar un nombre para la página Web para su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación.  
  
 Una vez que se ha especificado la página de publicación, la próxima vez que publique, se copiará en la ubicación de publicación; no se sobrescribirá si vuelve a publicar. Si desea personalizar la apariencia de la página, puede hacerlo sin preocuparse por perder los cambios. Para obtener más información, consulte [Cómo: personalizar la página Web predeterminada de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 El **página publicar** propiedad puede establecerse el **opciones de publicación** cuadro de diálogo, accesible desde el **publicar** panel de la **delDiseñadordeproyectos**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Para especificar una página Web personalizada para una aplicación ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **opciones** botón para abrir el **opciones de publicación** cuadro de diálogo.  
  
4.  Haga clic en **implementación**.  
  
5.  En el **opciones de publicación** diálogo cuadro, asegúrese de que el **implementación abrir la página web después de publicar** está seleccionada la casilla de verificación (debe estar seleccionado de forma predeterminada).  
  
6.  En el **página web de implementación:** cuadro, escriba el nombre de la página Web y, a continuación, haga clic en **Aceptar**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Para impedir que se inicie cada vez que publique la página de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Seleccione el **publicar** panel.  
  
3.  Haga clic en el **opciones** botón para abrir el **opciones de publicación** cuadro de diálogo.  
  
4.  Haga clic en **implementación**.  
  
5.  En el **opciones de publicación** cuadro de diálogo, desactive la **implementación abrir la página web después de publicar** casilla de verificación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Cómo: Personalizar la página web predeterminada para ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)




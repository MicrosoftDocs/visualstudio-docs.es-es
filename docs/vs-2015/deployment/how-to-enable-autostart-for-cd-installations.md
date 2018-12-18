---
title: 'Cómo: habilitar AutoStart para instalaciones con CD | Microsoft Docs'
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2fde610731ca5ec315b94d2e46f58edb2a7b56fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273148"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Cómo: Habilitar AutoStart para instalaciones con CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al implementar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación mediante medios extraíbles, como CD-ROM o DVD-ROM, puede habilitar `AutoStart` para que el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se inicia automáticamente cuando se inserta el disco.  
  
 `AutoStart` se puede habilitar en el **publicar** página de la **Diseñador de proyectos**.  
  
### <a name="to-enable-autostart"></a>Para habilitar el inicio automático  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **opciones** botón.  
  
     El **opciones de publicación** aparece el cuadro de diálogo.  
  
4.  Haga clic en **implementación**.  
  
5.  Seleccione el **instalaciones con CD para, se inicia automáticamente el programa de instalación al CD está insertado** casilla de verificación.  
  
     Cuando se publica la aplicación, se copiará un archivo Autorun.inf para la ubicación de publicación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)




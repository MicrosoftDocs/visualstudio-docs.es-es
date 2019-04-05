---
title: Filtrar Habilitar AutoStart para instalaciones con CD | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6266f487e2e0c66e532297c3fdae3fd3e5498052
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996134"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Filtrar Habilitar AutoStart para instalaciones con CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al implementar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación mediante medios extraíbles, como CD-ROM o DVD-ROM, puede habilitar `AutoStart` para que el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se inicia automáticamente cuando se inserta el disco.  
  
 `AutoStart` se puede habilitar en el **publicar** página de la **Diseñador de proyectos**.  
  
### <a name="to-enable-autostart"></a>Para habilitar el inicio automático  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  Haga clic en el botón **Opciones**.  
  
     El **opciones de publicación** aparece el cuadro de diálogo.  
  
4.  Haga clic en **implementación**.  
  
5.  Seleccione el **instalaciones con CD para, se inicia automáticamente el programa de instalación al CD está insertado** casilla de verificación.  
  
     Cuando se publica la aplicación, se copiará un archivo Autorun.inf para la ubicación de publicación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

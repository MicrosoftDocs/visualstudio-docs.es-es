---
title: 'Cómo: habilitar AutoStart para instalaciones con CD | Microsoft Docs'
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
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153783"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Cómo: Habilitar AutoStart para instalaciones con CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al implementar una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación mediante medios extraíbles, como un CD-ROM o un DVD-ROM, puede habilitar `AutoStart` para que la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se inicie automáticamente cuando se inserte el medio.  
  
 `AutoStart` se puede habilitar en la página **publicar** del **Diseñador de proyectos**.  
  
### <a name="to-enable-autostart"></a>Para habilitar AutoStart  
  
1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. Haga clic en el botón **Opciones** .  
  
     Aparece el cuadro de diálogo **Opciones de publicación** .  
  
4. Haga clic en **Implementación**.  
  
5. Active la casilla **para instalaciones de CD, iniciar automáticamente el programa de instalación al insertar el CD** .  
  
     Cuando se publique la aplicación, se copiará un archivo Autorun. inf en la ubicación de publicación.  
  
## <a name="see-also"></a>Consulte también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

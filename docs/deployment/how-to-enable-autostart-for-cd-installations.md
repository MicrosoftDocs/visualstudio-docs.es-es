---
title: 'Cómo: habilitar AutoStart para instalaciones con CD | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4359b863da56242bbe612fa0055690d9923a9ec4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600480"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Cómo: Habilitar AutoStart para instalaciones con CD
Al implementar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante medios extraíbles, como CD-ROM o DVD-ROM, puede habilitar `AutoStart` para que el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se inicia automáticamente cuando se inserta el disco.

 `AutoStart` se puede habilitar en el **publicar** página de la **Diseñador de proyectos**.

### <a name="to-enable-autostart"></a>Para habilitar el inicio automático

1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2.  Haga clic en la pestaña **Publicar**.

3.  Haga clic en el botón **Opciones**.

     El **opciones de publicación** aparece el cuadro de diálogo.

4.  Haga clic en **implementación**.

5.  Seleccione el **instalaciones con CD para, se inicia automáticamente el programa de instalación al CD está insertado** casilla de verificación.

     Un *Autorun.inf* archivo se copiará en la ubicación de publicación cuando se publica la aplicación.

## <a name="see-also"></a>Vea también
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
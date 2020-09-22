---
title: Habilitar AutoStart para instalaciones con CD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 28fa4830c3ea5ff840e0d58f6d31f718c28ec3fb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850948"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Cómo: Habilitar AutoStart para instalaciones con CD
Al implementar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación mediante medios extraíbles, como un CD-ROM o un DVD-ROM, puede habilitar `AutoStart` para que la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se inicie automáticamente cuando se inserte el medio.

 `AutoStart` se puede habilitar en la página **publicar** del **Diseñador de proyectos**.

### <a name="to-enable-autostart"></a>Para habilitar AutoStart

1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **Opciones** .

     Aparece el cuadro de diálogo **Opciones de publicación** .

4. Haga clic en **Implementación**.

5. Active la casilla **para instalaciones de CD, iniciar automáticamente el programa de instalación al insertar el CD** .

     Cuando se publique la aplicación, se copiará un archivo *Autorun. inf* en la ubicación de publicación.

## <a name="see-also"></a>Vea también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
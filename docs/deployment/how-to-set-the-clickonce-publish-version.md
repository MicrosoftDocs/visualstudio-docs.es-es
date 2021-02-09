---
title: Establecer la versión de publicación de ClickOnce | Microsoft Docs
description: Obtenga información sobre cómo establecer la propiedad versión de publicación de ClickOnce, que determina si la aplicación es una actualización.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885032"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Cómo: Establecer la versión de publicación de ClickOnce
La [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propiedad determina si la aplicación que se está publicando se tratará como una actualización. Cada vez que se incrementa la versión, la aplicación se publica como una actualización.

 La `Publish Version` propiedad se puede establecer en la página **publicar** del **Diseñador de proyectos**.

> [!NOTE]
> Existe una opción de proyecto que incrementará automáticamente la `Publish Version` propiedad cada vez que se publique la aplicación. esta opción está habilitada de forma predeterminada. Para obtener más información, vea [Cómo: incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Para cambiar la versión de publicación

1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el campo **versión de publicación** , incremente los números de versión **principal**, **secundaria**, de **compilación** o de **revisión** .

    > [!NOTE]
    > Nunca debe disminuir un número de versión; Si lo hace, podría producirse un comportamiento de actualización impredecible.

## <a name="see-also"></a>Vea también
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Cómo: incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
---
title: Procedimiento Establecer la publicación de ClickOnce versión | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2bd526203b777bafd77c79a4934d1f3e8754dee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406843"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedimiento Establecimiento de la versión de publicación de ClickOnce
El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propiedad determina si la aplicación que se está publicando se tratará como una actualización. Se incrementa cada versión del tiempo, la aplicación se publicará como una actualización.

 El `Publish Version` propiedad puede establecerse en el **publicar** página de la **Diseñador de proyectos**.

> [!NOTE]
> Hay una opción de proyecto que se incrementará automáticamente el `Publish Version` propiedad cada vez que se publica la aplicación; esta opción está habilitada de forma predeterminada. Para obtener más información, vea [Cómo: Incremento automático de la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Para cambiar la versión de publicación

1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En **Publicar versión** campo, se incrementa la **principales**, **menores**, **compilar**, o **revisión** versión números.

    > [!NOTE]
    > Nunca se debe disminuir un número de versión; por lo que al hacerlo podría provocar un comportamiento impredecible de actualización.

## <a name="see-also"></a>Vea también
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Cómo: Incremento automático de la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
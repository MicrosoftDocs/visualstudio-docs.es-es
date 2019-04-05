---
title: Filtrar Establecer la publicación de ClickOnce versión | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b082e92ffac43e48725285bc9fa9052dd82cfd92
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997343"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Filtrar Establecer la versión de publicación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` propiedad determina si la aplicación que se está publicando se tratará como una actualización. Se incrementa cada versión del tiempo, la aplicación se publicará como una actualización.  
  
 El `Publish Version` propiedad puede establecerse en el **publicar** página de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Hay una opción de proyecto que se incrementará automáticamente el `Publish Version` propiedad cada vez que se publica la aplicación; esta opción está habilitada de forma predeterminada. Para obtener más información, vea [Cómo: Incremento automático de la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Para cambiar la versión de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Publicar**.  
  
3.  En **Publicar versión** campo, se incrementa la **principales**, **menores**, **compilar**, o **revisión** versión números.  
  
    > [!NOTE]
    >  Nunca se debe disminuir un número de versión; por lo que al hacerlo podría provocar un comportamiento impredecible de actualización.  
  
## <a name="see-also"></a>Vea también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Cómo: Automáticamente incrementar la publicación de ClickOnce versión](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

---
title: 'Cómo: establecer el ClickOnce publicación versión | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a0f96a3837a2c3a05a8fac20a9b6e5d4448f9c7e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Cómo: Establecer la versión de publicación de ClickOnce
El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propiedad determina si la aplicación que se está publicando se tratará como una actualización. Se incrementa cada versión de tiempo, la aplicación se publicará como una actualización.  
  
 El `Publish Version` propiedad puede establecerse en el **publicar** página de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Hay una opción de proyecto que se incrementará automáticamente el `Publish Version` propiedad cada vez que se publica la aplicación; esta opción está habilitada de forma predeterminada. Para obtener más información, consulte [Cómo: incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Para cambiar la versión de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En **Publicar versión** , a continuación, incrementar el **principales**, **secundaria**, **generar**, o **revisión** versión números.  
  
    > [!NOTE]
    >  Nunca se debe disminuir un número de versión; por lo que al hacerlo podría provocar un comportamiento impredecible de actualización.  
  
## <a name="see-also"></a>Vea también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Cómo: Incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
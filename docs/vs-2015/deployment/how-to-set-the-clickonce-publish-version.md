---
title: 'Cómo: establecer la versión de publicación de ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: ec5d5d742b5a0749d1d5d52cee0a0545dd8570f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842671"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Cómo: Establecer la versión de publicación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` propiedad determina si la aplicación que se está publicando se tratará como una actualización. Cada vez que se incrementa la versión, la aplicación se publica como una actualización.  
  
 La `Publish Version` propiedad se puede establecer en la página **publicar** del **Diseñador de proyectos**.  
  
> [!NOTE]
> Existe una opción de proyecto que incrementará automáticamente la `Publish Version` propiedad cada vez que se publique la aplicación. esta opción está habilitada de forma predeterminada. Para obtener más información, vea [Cómo: incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Para cambiar la versión de publicación  
  
1. Con un proyecto seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. En el campo **versión de publicación** , incremente los números de versión **principal**, **secundaria**, de **compilación**o de **revisión** .  
  
    > [!NOTE]
    > Nunca debe disminuir un número de versión; Si lo hace, podría producirse un comportamiento de actualización impredecible.  
  
## <a name="see-also"></a>Consulte también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Cómo: incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

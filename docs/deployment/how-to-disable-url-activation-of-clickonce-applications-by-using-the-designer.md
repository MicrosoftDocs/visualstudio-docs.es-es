---
title: "Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d4df4bab3b3dd7ed29dd3e5d3ca2ff7e56c1922d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Cómo: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador
Normalmente, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se iniciará automáticamente inmediatamente después de que se instale desde un servidor Web. Por motivos de seguridad, puede decidir deshabilitar este comportamiento e indicar a los usuarios para iniciar la aplicación desde el **iniciar** menú en su lugar. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.  
  
 Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede utilizar para las aplicaciones solo en línea, que se pueden iniciar únicamente mediante su dirección URL. Para obtener más información acerca de las diferencias entre las aplicaciones solo en línea e instaladas, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimiento se utiliza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. También puede realizar esta tarea mediante la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obtener más información, consulte [Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedimiento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación  
  
1.  Haga clic en el nombre del proyecto en **el Explorador de soluciones**y haga clic en **propiedades**.  
  
2.  En el **propiedades** página, haga clic en el **publicar** ficha.  
  
3.  Haga clic en **Opciones**.  
  
4.  Haga clic en **manifiestos**.  
  
5.  Active la casilla de verificación **bloquea la aplicación desde la que se activa mediante una dirección URL**.  
  
6.  Implemente su aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
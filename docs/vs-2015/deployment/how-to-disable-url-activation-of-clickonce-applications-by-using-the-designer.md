---
title: 'Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cc5571dffba9daa3ac1f5f78e354487cbc654fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576032"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Cómo: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: deshabilitar la dirección URL de activación de aplicaciones ClickOnce mediante el diseñador](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer).  
  
Normalmente, un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se iniciará automáticamente inmediatamente después de instalarlo desde un servidor Web. Por motivos de seguridad, puede decidir deshabilitar este comportamiento e indicar a los usuarios para iniciar la aplicación desde el **iniciar** menú en su lugar. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.  
  
 Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede usar para las aplicaciones sólo en línea, que se pueden iniciar utilizando su dirección URL. Para obtener más información sobre la diferencia entre las aplicaciones sólo en línea e instaladas, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimiento utiliza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. También puede realizar esta tarea mediante el uso de la [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Para obtener más información, consulte [Cómo: deshabilitar la dirección URL de activación de las aplicaciones ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedimiento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación  
  
1.  Haga clic en el nombre del proyecto en **el Explorador de soluciones**y haga clic en **propiedades**.  
  
2.  En el **propiedades** página, haga clic en el **publicar** ficha.  
  
3.  Haga clic en **Opciones**.  
  
4.  Haga clic en **manifiestos**.  
  
5.  Seleccione la casilla de verificación con la etiqueta **bloquear la aplicación desde la que se activa mediante una dirección URL**.  
  
6.  Implemente su aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)




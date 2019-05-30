---
title: Deshabilitar la activación de la dirección URL de las aplicaciones ClickOnce mediante el diseñador
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8296f08c29b3259c19393a860ee34f6c3f05a42
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263276"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedimiento Desactivación de la activación de URL de aplicaciones ClickOnce mediante el diseñador
Normalmente, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se iniciará automáticamente inmediatamente después de instalarlo desde un servidor Web. Por motivos de seguridad, puede decidir deshabilitar este comportamiento e indicar a los usuarios para iniciar la aplicación desde el **iniciar** menú en su lugar. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.

 Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede usar para las aplicaciones sólo en línea, que se pueden iniciar utilizando su dirección URL. Para obtener más información sobre la diferencia entre las aplicaciones sólo en línea e instaladas, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Este procedimiento utiliza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. También puede realizar esta tarea mediante el uso de la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obtener más información, vea [Cómo: Desactivación de la activación de URL de aplicaciones ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedimiento

#### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación

1. Haga clic en el nombre del proyecto en **el Explorador de soluciones**y haga clic en **propiedades**.

2. En el **propiedades** página, haga clic en el **publicar** ficha.

3. Haga clic en **Opciones**.

4. Haga clic en **manifiestos**.

5. Seleccione la casilla de verificación con la etiqueta **bloquear la aplicación desde la que se activa mediante una dirección URL**.

6. Implemente su aplicación.

## <a name="see-also"></a>Vea también
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
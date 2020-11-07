---
title: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador
description: Obtenga información sobre cómo deshabilitar el inicio automático al instalar para una aplicación ClickOnce con Visual Studio, de modo que los usuarios deben iniciar la aplicación desde el menú Inicio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: c243b0e0565c082e05fd15a1e02aa0507120e16b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350015"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Cómo: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce mediante el diseñador
Normalmente, una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se iniciará automáticamente inmediatamente después de instalarla desde un servidor Web. Por motivos de seguridad, puede decidir deshabilitar este comportamiento e indicar a los usuarios que inicien la aplicación desde el menú **Inicio** en su lugar. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.

 Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede usar para aplicaciones solo en línea, que solo se pueden iniciar mediante su dirección URL. Para obtener más información acerca de la diferencia entre las aplicaciones solo en línea y las instaladas, vea [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 En este procedimiento se usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . También puede realizar esta tarea mediante el [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Para obtener más información, vea [Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedimiento

#### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación

1. Haga clic con el botón secundario en el nombre del proyecto en **Explorador de soluciones** y haga clic en **propiedades**.

2. En la página **propiedades** , haga clic en la pestaña **publicar** .

3. Haga clic en **Opciones**.

4. Haga clic en **manifiestos**.

5. Active la casilla **de verificación bloquear la aplicación para que no se active a través de una dirección URL**.

6. Implementación de aplicación.

## <a name="see-also"></a>Vea también
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
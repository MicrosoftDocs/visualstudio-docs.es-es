---
title: Incorporación al Portal de administración de suscripciones de Visual Studio después de migrar la organización
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 07/12/2018
Ms.topic: Get-Started-Article
Description: Learn how to successfully onboard your organization for Visual Studio subscriptions after migrating to the administration portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 0740abb865856470b80d0706794f8e49423e72b2
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443524"
---
# <a name="onboard-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>Incorporación al Portal de administración de suscripciones de Visual Studio después de migrar la organización 

Si administró suscripciones de Visual Studio en el Centro de servicios de licencias por volumen (VLSC) de Microsoft y ha visitado recientemente el sitio para administrar suscripciones, observará que la administración de suscripciones ya no está disponible en el VLSC. El proceso para administrar las suscripciones tendría este aspecto:
> [!div class="mx-imgBorder"]
> ![Captura de pantalla de VLSC de Microsoft, con la pestaña Suscripciones resaltada](_img/post-migration-onboarding/vlsc-subscriptions.png)

Sin embargo, las suscripciones se administran ahora mediante un nuevo portal llamado el Portal de administración de suscripciones de Visual Studio. Normalmente, el contacto principal o para notificaciones con respecto al contrato de licencias por volumen de la organización completa este proceso. Si no es así, la siguiente información le ayuda a acceder a la administración de suscripciones. 

Se pueden dar varios casos:
1.  [El contacto principal no completó el proceso de incorporación.](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [El contacto principal completó la incorporación, pero no lo agregó como administrador. Las credenciales se mostraron en VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [El contacto principal completó la incorporación, pero no lo agregó como administrador. Las credenciales no se mostraron en VLSC.](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> Si usted es el contacto principal o el contacto para notificaciones y no completó el proceso de incorporación, deberá seguir los pasos del escenario 1 para configurar su organización. 

En las secciones siguientes se proporcionan más detalles sobre estos casos. 

## <a name="onboarding-not-completed-by-primary-contact"></a>Incorporación no completada por el contacto principal

Si el contacto principal no completó la experiencia de incorporación, aparecerá la pantalla siguiente. Si tiene acceso al [Centro de servicios de licencias por volumen (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), puede completar este proceso y obtener acceso para administrar las suscripciones. Necesitará el [número de cliente público (PCN)](find-pcn.md) de su organización, que puede encontrarse en el VLSC. 

En el campo PCN, escriba el [PCN](find-pcn.md) y seleccione **Enviar una invitación por correo electrónico**. 
> [!div class="mx-imgBorder"]
> ![Captura de pantalla del Portal de administración de suscripciones de Visual Studio](_img/post-migration-onboarding/send-invitation.png)

Recibirá un correo electrónico con un vínculo único para completar el proceso de incorporación. Haga clic en el vínculo del correo electrónico, inicie sesión con su dirección de correo electrónico y, una vez más, escriba el PCN. El vínculo único del correo electrónico es lo que permite obtener acceso al Portal de administración de suscripciones de Visual Studio. Después puede acceder a las suscripciones y administrarlas. 
> [!div class="mx-imgBorder"]
> ![Captura de pantalla de notificación correcta](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>El contacto principal no ha proporcionado acceso de administrador

Si su contacto principal completó el proceso de incorporación y las credenciales estaban anteriormente en el VLSC, pero dicho contacto no le proporcionó acceso, verá la siguiente notificación. Para convertirse en administrador, póngase en contacto con uno de los superadministradores de la organización mostrados en la notificación.
> [!div class="mx-imgBorder"]
> ![Captura de pantalla del Portal de administración de suscripciones de Visual Studio, con una lista de superadministradores](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Las credenciales no aparecían en el VLSC antes de la migración

Si el contacto principal completó la incorporación, pero no lo agregó como usuario y sus credenciales no aparecían anteriormente en el VLSC, verá la siguiente notificación. Llegue a su [contacto principal](find-primary-contact.md) para tener acceso al portal. 
> [!div class="mx-imgBorder"]
> ![Captura de pantalla del Portal de administración de suscripciones de Visual Studio, con la notificación "no podemos encontrarle"](_img/post-migration-onboarding/cant-find-you.png)
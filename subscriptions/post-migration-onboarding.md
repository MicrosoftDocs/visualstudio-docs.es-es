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
ms.openlocfilehash: 4052d04669327ab0383aba91de05e4d8b95db4c5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637460"
---
# <a name="onboarding-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>Incorporación al Portal de administración de suscripciones de Visual Studio después de migrar la organización 

Si administró suscripciones de Visual Studio en el Centro de servicios de licencias por volumen (VLSC) y ha visitado recientemente el sitio para administrar suscripciones, observará que la administración de suscripciones ya no está disponible en el VLSC. El proceso para administrar las suscripciones tendría este aspecto:
> [!div class="mx-imgBorder"]
> ![Suscripciones de VLSC](_img/post-migration-onboarding/vlsc-subscriptions.png)

Tras la que llegada a la página suscripciones, es probable que haga clic en el vínculo siguiente. 
> [!div class="mx-imgBorder"]
> ![Vínculo de resumen de relación](_img/post-migration-onboarding/relationship-summary-link.png)

Este vínculo le habría llevado anteriormente a la página donde podría administrar las suscripciones.   Sin embargo, las suscripciones se administran ahora mediante un nuevo portal llamado el Portal de administración de suscripciones de Visual Studio.  Existen varios pasos que debe realizar el contacto principal o para notificaciones con respecto al acuerdo de licencias por volumen de la organización. En caso de que dicho contacto no haya completado este proceso, o ya no esté disponible, pueden ocurrir varias cosas. Los siguientes pasos le guían en el proceso de obtener acceso a la administración de suscripciones. 

Se pueden dar varios casos:
1.  [El contacto principal no completó el proceso de incorporación](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [El contacto principal completó la incorporación, pero no lo agregó como administrador.  Las credenciales se mostraron en VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [El contacto principal completó la incorporación, pero no lo agregó como administrador y sus credenciales no se mostraron en el VLSC](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration).  

<sup>1</sup> Si usted es el contacto principal o el contacto para notificaciones y no completó el proceso de incorporación, deberá seguir los pasos del escenario 1 para configurar su organización. 

Los siguientes son ejemplos de las pantallas que podría ver y los pasos que puede realizar, en cada caso. 

## <a name="onboarding-not-completed-by-primary-contact"></a>Incorporación no completada por el contacto principal

Si el contacto principal no completó la experiencia de incorporación, podría ver la pantalla siguiente. Si tiene acceso al [Centro de servicios de licencias por volumen (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), podrá completar este proceso y obtener acceso para administrar las suscripciones. Necesitará el [número de cliente público (PCN)](find-pcn.md) de su organización, que puede encontrarse en el VLSC. 

Si el contacto principal se completó el proceso de incorporación, simplemente escriba el [PCN](find-pcn.md) en el campo y seleccione "Enviar invitación". 
> [!div class="mx-imgBorder"]
> ![Envío de correo electrónico de invitación](_img/post-migration-onboarding/send-invitation.png)

Una vez que haya hecho clic en el botón para enviar la invitación, recibirá un correo electrónico con un vínculo único para completar el proceso de incorporación. Deberá haga clic en el vínculo del correo electrónico, iniciar sesión con su dirección de correo electrónico y, una vez más, escribir el PCN. El vínculo único del correo electrónico es lo que permite obtener acceso al Portal de administración de suscripciones de Visual Studio. Luego, podrá acceder a las suscripciones y administrarlas. 
> [!div class="mx-imgBorder"]
> ![Correo electrónico correcto](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>El contacto principal no ha proporcionado acceso de administrador

Si su contacto principal completó el proceso de incorporación y las credenciales estaban anteriormente en el VLSC, pero el contacto principal no le proporcionó acceso, verá la siguiente notificación al iniciar sesión en el [Portal de administración de suscripciones de Visual Studio](https://manage.visualstudio.com/).  Para convertirse en administrador, deberá ponerse en contacto con uno de los superadministradores de la organización mostrados en la pantalla.
> [!div class="mx-imgBorder"]
> ![Lista de administradores](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Las credenciales no aparecían en el VLSC antes de la migración

Si el contacto principal completó la incorporación, pero no lo agregó como usuario y sus credenciales no aparecían anteriormente en el VLSC, verá la siguiente notificación al intentar acceder al [Portal de administración de suscripciones de Visual Studio](https://manage.visualstudio.com/). Necesitará llegar a su [contacto principal](find-primary-contact.md) para tener acceso al portal. 
> [!div class="mx-imgBorder"]
> ![No le encontramos](_img/post-migration-onboarding/cant-find-you.png)
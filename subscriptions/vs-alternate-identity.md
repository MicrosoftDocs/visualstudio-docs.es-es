---
title: Identidades de los suscriptores de Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identidades de los suscriptores de Visual Studio

Cuando activa una suscripción de Visual Studio, vinculamos la identidad (o inicio de sesión) que ha usado durante la activación con la suscripción de Visual Studio. De esta manera, podremos reconocerle en el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), en VSTS y en Azure.

En VSTS, comprobamos el estado de la suscripción de Visual Studio cada vez que inicia sesión y le concederemos características automáticamente dentro del ámbito de cada cuenta de la que sea miembro. Dado que estas características se incluyen como una ventaja de suscriptor, no supone un gasto extra incluirle como miembro de una cuenta de VSTS si usa una identidad que está vinculada a su suscripción de Visual Studio.

En Azure, comprobamos el estado de la suscripción de Visual Studio cuando se activa su [crédito mensual de Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), que es una ventaja de suscriptor.

En el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) puede agregar una **identidad alternativa** además de la identidad que usó durante la activación. Actualmente, le permitimos agregar una identidad alternativa si ha usado una cuenta Microsoft para activar su suscripción. De este modo, puede agregar también una cuenta profesional o educativa (que use para iniciar sesión en Visual Studio, en Office 365 o en la red de la empresa o del centro educativo), lo que le permitirá tener acceso a VSTS tanto a través de su cuenta personal como de su cuenta profesional o educativa.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Cómo agregar una identidad alternativa a su suscripción de Visual Studio

1. Inicie sesión en el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Si se le pide que elija entre "cuenta personal" o "cuenta profesional o educativa", elija "cuenta personal" (su cuenta Microsoft).
  >
  > A veces hay que escoger porque la cuenta Microsoft y la cuenta profesional o educativa comparten la misma dirección de correo electrónico. Aunque ambas identidades emplean la misma dirección de correo electrónico, siguen siendo identidades independientes con perfiles, configuraciones de seguridad y permisos distintos.
  >
  > A partir del 30 de marzo de 2018, ya no se podrá crear una cuenta Microsoft con un correo electrónico que use un dominio administrado en Azure Active Directory. Sí se podrá iniciar sesión usando ese correo electrónico como una cuenta profesional.

2. Vaya a la pestaña **Suscripciones**.

  ![Seleccione Suscripciones.](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. En **Vínculos relacionados**, vaya a **Agregar cuenta alternativa**.

  ![En Vínculos relacionados, vaya a Agregar cuenta alternativa.](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Indique su cuenta profesional o educativa y seleccione **Agregar**.

  ![Indique su cuenta profesional o educativa.](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Use la cuenta profesional o educativa para iniciar sesión en su cuenta de VSTS (```https://{youraccount}.visualstudio.com```). La información puede tardar un poco en propagarse; compruébelo 15 minutos más tarde. 

## <a name="faq"></a>Preguntas más frecuentes

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>P: ¿Por qué VSTS no me reconoce como suscriptor de Visual Studio?
R: VSTS debería reconocer la suscripción automáticamente cuando inicie sesión con su identidad principal o alternativa. Si no es así, puede probar a hacer lo siguiente:

* Compruebe que tiene una suscripción de Visual Studio activa que [incluye VSTS como ventaja](vs-vsts.md).

* Confirme que está usando un inicio de sesión/identidad que es la identidad principal o alternativa de su suscripción de Visual Studio.

* Vaya al [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) al menos una vez antes de iniciar sesión en VSTS.

Si VSTS sigue sin reconocer la suscripción, [póngase en contacto con el equipo de soporte técnico](https://www.visualstudio.com/team-services/support/).


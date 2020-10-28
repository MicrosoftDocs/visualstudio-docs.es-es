---
title: Aparición de correos electrónicos personales en Microsoft Business Center
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 09/22/2020
ms.topic: conceptual
description: 'Suscripciones de Visual Studio: ¿por qué aparecen direcciones de Hotmail o Gmail para mis suscriptores?'
ms.openlocfilehash: dc2de6c852f39f789fb07358384ad490d13f137c
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "91022676"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Suscripciones de Visual Studio: ¿por qué mis suscriptores tienen cuentas personales?
A medida que las empresas se migran del Centro de servicios de licencias por volumen (VLSC) al nuevo [Portal de administración de suscripciones](https://manage.visualstudio.com) de Visual Studio, los administradores pueden sorprenderse de ver que la "dirección de correo electrónico de inicio de sesión" de algunos suscriptores es una dirección de correo electrónico personal, como Hotmail o Outlook.  

## <a name="cause"></a>Motivo
Esta situación puede darse como consecuencia de los procesos de inicio de sesión asociados a la anterior experiencia de suscriptor de MSDN. Los usuarios se migraron desde Microsoft Business Center hasta el Portal de administración de suscripciones de Visual Studio sin modificaciones. Es posible que algunos administradores no se hayan percatado de que los usuarios habían estado utilizando cuentas personales para acceder a los beneficios de su suscripción. Antes de las migraciones de suscriptores de Visual Studio, que se completaron en 2016, se requerían dos acciones para usar correctamente una suscripción a Visual Studio:
1. El administrador "asignaba" la suscripción a un suscriptor individual, que usaba su dirección de correo electrónico profesional o educativa.
2. El suscriptor "activaba" la suscripción.

Durante el proceso de activación del suscriptor: Se requería una cuenta Microsoft (MSA) para iniciar sesión. En caso de que el suscriptor no intentara usar su cuenta profesional o educativa (por ejemplo, tasha@contoso.com) como MSA, este podía crear una nueva cuenta o aprovechar alguna existente. Como resultado, la "dirección de correo electrónico de inicio de sesión" no coincidía con la "dirección de asignación".

> [!NOTE]
> La experiencia moderna de suscriptor en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) admite los tipos de identidad profesional/educativa y de cuenta Microsoft (MSA).

## <a name="solution"></a>Soluciones
Para corregir el problema, simplemente seleccione el botón **Connect Emails** (Conectar correos electrónicos) y el sistema intentará correlacionar las cuentas de Microsoft y los usuarios existentes de la instancia de Azure Active Directory (Azure AD) de la organización en función del nombre y el apellido. Si se produce un error en una asociación, puede hacer clic en la **X** situada a la derecha de la asociación para quitarla.  

Vea este vídeo o siga leyendo para saber cómo solucionarlo. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Botón Conectar correos electrónicos](_img/connect-emails/connect-emails-button.png "Haga clic en Connect Emails (Conectar correos electrónicos) para que sus usuarios con cuentas de Microsoft coincidan con los de Azure Active Directory.")

También puede **buscar en el directorio** para corregir los errores o rellenar la información que falta de su Azure AD. Si todas las coincidencias son correctas, puede elegir el botón **Current identity** (Identidad actual) para seleccionar todas las entradas coincidentes en lugar de seleccionarlas de una en una.  

> [!div class="mx-imgBorder"]
> ![Ventana Conectar correos electrónicos](_img/connect-emails/connect-emails-flyout.png "Seleccione los suscriptores que quiere que coincidan con sus identidades de Azure AD y haga clic en Continue (Continuar).")

A continuación, haga clic en **Continue** (Continuar) para ir a una lista de los cambios que van a realizarse. Si está de acuerdo, haga clic en **Save** (Guardar) y se aplicarán los cambios. El suscriptor también recibirá un mensaje que le informa del cambio la próxima vez que inicie sesión en su suscripción.  Observe que en esta lista solo aparecen los dos suscriptores que coincidían en Azure Active Directory.  En nuestro ejemplo, como Frederick no tenía una dirección correspondiente en Azure AD, su cuenta de Microsoft (MSA) no coincidía con una cuenta profesional. 

> [!div class="mx-imgBorder"]
> ![Confirmación de conexión de correos electrónicos](_img/connect-emails/connect-emails-confirm.png "Haga clic en Continue (Continuar) para implementar los cambios propuestos y, luego, en Save (Guardar).") 

> [!NOTE]
> Al editar la dirección de correo electrónico de inicio de sesión, solo se actualiza la dirección que usa el suscriptor para iniciar sesión en su suscripción en https://my.visualstudio.com. Si el suscriptor ha usado las otras direcciones de correo electrónico para activar beneficios como Azure o Pluralsight, deberá seguir usando esas direcciones de correo electrónico para acceder a ellos. Si acceden a nuevas ventajas, deberán usar la nueva dirección de correo electrónico. 

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

##  <a name="next-steps"></a>Pasos siguientes
- Si ha actualizado las direcciones de correo electrónico de los suscriptores, debería informarles de que ha cambiado su información de inicio de sesión.  También recibirán un correo electrónico con esa información actualizada.
- Puede ser útil [filtrar la lista de suscriptores](search-license.md) de su organización para buscar cualquier dirección de correo electrónico de inicio de sesión que deba cambiar.
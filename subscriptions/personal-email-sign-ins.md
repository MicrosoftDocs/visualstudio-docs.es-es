---
title: Aparición de correos electrónicos personales en Microsoft Business Center
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/17/2020
ms.topic: conceptual
description: 'Suscripciones de Visual Studio: ¿por qué aparecen direcciones de Hotmail o Gmail para mis suscriptores?'
ms.openlocfilehash: 7cd6a4761efb7dcad7568bd0a95ba33141407055
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "79550334"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Suscripciones de Visual Studio: ¿por qué mis suscriptores tienen cuentas personales?
A medida que las empresas se migran del Centro de servicios de licencias por volumen (VLSC) al nuevo [Portal de administración de suscripciones](https://manage.visualstudio.com) de Visual Studio, los administradores pueden sorprenderse de ver que la "dirección de correo electrónico de inicio de sesión" de algunos suscriptores es una dirección de correo electrónico personal, como Hotmail o Outlook.  Para obtener más información, consulte [este vídeo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Motivo
Esta situación puede darse como consecuencia de los procesos de inicio de sesión asociados a la anterior experiencia de suscriptor de MSDN. Los usuarios se migraron desde Microsoft Business Center hasta el Portal de administración de suscripciones de Visual Studio sin modificaciones. Es posible que algunos administradores no se hayan percatado de que los usuarios habían estado utilizando cuentas personales para acceder a los beneficios de su suscripción. Antes de las migraciones de suscriptores de Visual Studio, que se completaron en 2016, se requerían dos acciones para usar correctamente una suscripción a Visual Studio:
1. El administrador "asignaba" la suscripción a un suscriptor individual, que usaba su dirección de correo electrónico profesional o educativa.
2. El suscriptor "activaba" la suscripción.

Durante el proceso de activación del suscriptor: Se requería una cuenta Microsoft (MSA) para iniciar sesión. En caso de que el suscriptor no intentara usar su cuenta profesional o educativa (por ejemplo, tasha@contoso.com) como MSA, este podía crear una nueva cuenta o aprovechar alguna existente. Como resultado, la "dirección de correo electrónico de inicio de sesión" no coincidía con la "dirección de asignación".

> [!NOTE]
> La experiencia moderna de suscriptor en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) admite los tipos de identidad profesional/educativa y de cuenta Microsoft (MSA).

## <a name="solution"></a>Soluciones
Para corregir el problema, simplemente seleccione el botón **Connect Emails** (Conectar correos electrónicos) y el sistema intentará correlacionar las cuentas de Microsoft y los usuarios existentes de la instancia de Azure Active Directory (Azure AD) de la organización en función del nombre y el apellido. Si se produce un error en una asociación, puede hacer clic en la **X** situada a la derecha de la asociación para quitarla.  

> [!div class="mx-imgBorder"]
> ![Botón Conectar correos electrónicos](_img/connect-emails/connect-emails-button.png)

También puede **buscar en el directorio** para corregir los errores o rellenar la información que falta de su Azure AD. Si todas las asociaciones son correctas, puede elegir "Select all matched subscribers" (Seleccionar todos los suscriptores coincidentes), en lugar de seleccionarlos de uno en uno.  

> [!div class="mx-imgBorder"]
> ![Ventana Conectar correos electrónicos](_img/connect-emails/connect-emails-flyout.png)

A continuación, haga clic en "Continue" (Continuar) para ir a una pantalla en la que se describen los cambios que van a realizarse. Si está de acuerdo, haga clic en "Save" (Guardar) y se aplicarán los cambios. El suscriptor también recibirá un mensaje que le informa del cambio la próxima vez que inicie sesión en su suscripción.   

> [!div class="mx-imgBorder"]
> ![Confirmación de conexión de correos electrónicos](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Al editar la dirección de correo electrónico de inicio de sesión, solo se actualiza la dirección que usa el suscriptor para iniciar sesión en su suscripción en https://my.visualstudio.com. Si el suscriptor ha usado las otras direcciones de correo electrónico para activar beneficios como Azure o Pluralsight, deberá seguir usando esas direcciones de correo electrónico para acceder a ellos. Si acceden a nuevas ventajas, deberán usar la nueva dirección de correo electrónico. 

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Pasos siguientes
- Si ha actualizado las direcciones de correo electrónico de los suscriptores, debería informarles de que ha cambiado su información de inicio de sesión.  También recibirán un correo electrónico con esa información actualizada.
- Puede ser útil [filtrar la lista de suscriptores](search-license.md) de su organización para buscar cualquier dirección de correo electrónico de inicio de sesión que deba cambiar.  

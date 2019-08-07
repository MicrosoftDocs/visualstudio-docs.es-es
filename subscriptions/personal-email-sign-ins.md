---
title: Aparición de correos electrónicos personales en Microsoft Business Center
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 'Suscripciones de Visual Studio: ¿por qué aparecen direcciones de Hotmail o Gmail para mis suscriptores?'
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605756"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Suscripciones de Visual Studio: ¿por qué aparecen direcciones de Hotmail o Gmail para mis suscriptores?
A medida que las empresas se migran de Microsoft Business Center al nuevo [Portal de administración de suscripciones](https://manage.visualstudio.com) de Visual Studio, los administradores pueden sorprenderse de ver que la "dirección de correo electrónico de inicio de sesión" de algunos suscriptores es una dirección de correo electrónico de otro proveedor, como Hotmail, Gmail o Yahoo.  Para obtener más información, consulte [este vídeo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Motivo
Esta situación puede darse como consecuencia de los procesos de inicio de sesión asociados a la anterior experiencia de suscriptor de MSDN. Los usuarios se migraron desde Microsoft Business Center hasta el Portal de administración de suscripciones de Visual Studio sin modificaciones. Es posible que algunos administradores no se hayan percatado de que los usuarios habían estado utilizando cuentas personales para acceder a los beneficios de su suscripción. Antes de las migraciones de suscriptores de Visual Studio, que se completaron en 2016, se requerían dos acciones para usar correctamente una suscripción a Visual Studio:
1. El administrador "asignaba" la suscripción a un suscriptor individual, que usaba su dirección de correo electrónico profesional o educativa.
2. El suscriptor "activaba" la suscripción.

Durante el proceso de activación del suscriptor: Se requería una cuenta Microsoft (MSA) para iniciar sesión. En caso de que el suscriptor no intentara usar su cuenta profesional o educativa (por ejemplo, tasha@contoso.com) como MSA, este podía crear una nueva cuenta o aprovechar alguna existente. Como resultado, la "dirección de correo electrónico de inicio de sesión" no coincidía con la "dirección de asignación".

> [!NOTE]
> La nueva experiencia de suscriptor en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) admite los tipos de identidad profesional/educativa y de cuenta Microsoft (MAA).

Por último, debido a que la migración del administrador toma datos de Microsoft Business Center con respecto a la "dirección de correo electrónico de inicio de sesión" del suscriptor para completar la nueva experiencia de administración de los suscriptores, los administradores recientemente migrados podrían haber visto estas cuentas personales, que previamente no habían advertido, debido a algunos cambios en la interfaz de usuario que hace esta información más visible.

## <a name="solution"></a>Soluciones
Para corregir el problema, debe modificar la información del suscriptor para actualizar sus direcciones de correo electrónico de inicio de sesión.  Las modificaciones pueden hacerse de una en una o todas a la vez. Para más información, visite [Edición de suscripciones](edit-license.md).

##  <a name="next-steps"></a>Pasos siguientes
- Si ha actualizado las direcciones de correo electrónico de los suscriptores, debería informarles de que ha cambiado su información de inicio de sesión.  También recibirán un correo electrónico con esa información actualizada.
- Puede ser útil [filtrar la lista de suscriptores](search-license.md) de su organización para buscar cualquier dirección de correo electrónico de inicio de sesión que deba cambiar.  


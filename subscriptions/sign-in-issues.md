---
title: Problemas al iniciar sesión en suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 02/19/2021
ms.topic: conceptual
description: Obtenga información sobre los problemas que pueden surgir al iniciar sesión en suscripciones de Visual Studio
ms.openlocfilehash: 5735e0c4178e6866539fff2edac6155642a1ba73
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607202"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problemas al iniciar sesión en las suscripciones de Visual Studio
Para usar su suscripción de Visual Studio, primero debe iniciar sesión.  Según la suscripción, es posible que la configurase con una cuenta Microsoft (MSA) o una identidad de Azure Active Directory (AAD).  En este artículo se describen algunos de los problemas que pueden surgir al iniciar sesión en su suscripción.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>No se pueden crear cuentas Microsoft (MSA) con direcciones de correo electrónico profesionales o educativas
Ya no se permite crear una nueva cuenta Microsoft (MSA) personal con una dirección de correo electrónico profesional o educativa cuando se configura el dominio de correo electrónico en Azure AD. ¿Qué significa? Si la organización usa Microsoft 365 u otros servicios empresariales de Microsoft que se basan en Azure AD y si ha agregado un nombre de dominio al inquilino de Azure AD, los usuarios ya no podrán crear una cuenta personal de Microsoft con una dirección de correo electrónico en su dominio.

### <a name="why-was-this-change-made"></a>¿Por qué se realizó este cambio?
Tener una cuenta Microsoft personal con una dirección profesional como nombre de usuario causa muchos problemas a los usuarios finales y departamentos de TI por igual. Por ejemplo:
- Los usuarios podrían pensar que su cuenta Microsoft personal cumple los requisitos empresariales y que mantienen el cumplimiento cuando guardan documentos empresariales en su OneDrive
- Los usuarios que dejen la organización generalmente perderán el acceso a su dirección de correo electrónico profesional. Cuando lo hagan, es posible que no puedan volver a acceder a su cuenta personal de Microsoft si olvidan su contraseña. Por otro lado, su departamento de TI podría restablecer las contraseñas y acceder a la cuenta personal de antiguos empleados.
- Los departamentos de TI tienen una falsa sensación de seguridad y de propiedad de las cuentas. Pero los usuarios solo necesitan enviar un código a su correo electrónico profesional una vez y podrán cambiar el nombre de su cuenta en cualquier momento en el futuro.

La situación es especialmente confusa para los usuarios que tienen dos cuentas con la misma dirección de correo electrónico (una en Azure AD y una cuenta Microsoft).

### <a name="what-does-this-experience-look-like"></a>¿Qué aspecto tiene esta experiencia?
Si intenta registrarse en una aplicación de consumidor de Microsoft con una dirección de correo electrónico profesional o educativa, verá el siguiente mensaje.

   > [!div class="mx-imgBorder"]
   > ![No se puede crear una cuenta con el correo electrónico profesional](_img/sign-in-issues/cannot-use-work-email.png "Proporcione un nombre de usuario y una contraseña para crear la cuenta.")

Pero si intenta registrarse en una aplicación de Microsoft que admite cuentas personales, profesionales o educativas, debería ver este mensaje:

   > [!div class="mx-imgBorder"]
   > ![Se admiten cuentas profesionales o educativas](_img/sign-in-issues/existing-account.png "Aquí no puede suscribirse con una dirección de correo electrónico profesional o educativa.")

### <a name="are-existing-accounts-affected"></a>¿Se ven afectadas las cuentas existentes?
El bloqueo de registro descrito aquí solo impide la creación de nuevas cuentas. No tiene ningún impacto en los usuarios que ya tienen una cuenta Microsoft con una dirección de correo electrónico profesional o educativa. Si ya están en esta situación, hemos facilitado el proceso de cambiar el nombre de una cuenta Microsoft personal. Este [artículo de soporte técnico](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) proporciona instrucciones paso a paso sencillas. Cambiar el nombre de la cuenta Microsoft personal implica cambiar el nombre de usuario y no afecta a su correo electrónico profesional o a cómo inicia sesión en servicios para la empresa, como Microsoft 365. Tampoco afecta a su información personal, solo cambia la manera de iniciar sesión en ella. Puede usar otra dirección de correo electrónico (personal), obtener una nueva dirección de correo electrónico de @outlook.com de Microsoft, o usar su número de teléfono como un nuevo nombre de usuario.

> [!NOTE]
> Si el departamento de TI le pide que cree una cuenta Microsoft personal con su correo electrónico profesional o educativo, por ejemplo, para obtener acceso a servicios para la empresa de Microsoft como soporte técnico Premier, hable con su equipo de administración antes de cambiar el nombre de su cuenta.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Eliminar una dirección de inicio de sesión puede impedir el acceso a una suscripción
Si elimina una o más identidades (MSA o AAD) asociadas con su suscripción, la información de suscriptor, incluido su nombre de usuario y el id. de inicio de sesión, se puede transformar en datos anónimos, lo que provocará la pérdida de acceso a su suscripción.

Para evitar impactos en su acceso a la suscripción, use una de estas técnicas.
- Implemente un sistema de administración de identidad único, ya sea MSA o AAD, pero no ambos.
- Asocie las identidades de AAD y MSA a través de los inquilinos.

## <a name="signing-in-may-fail-when-using-aliases"></a>Puede producirse un error al iniciar sesión mediante alias
Según el tipo de cuenta utilizada para iniciar sesión, es posible que las suscripciones disponibles no se muestren correctamente al iniciar sesión en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una posible causa es el uso de "alias" o "nombres descriptivos" en lugar de la identidad de inicio de sesión a la que está asignada la suscripción. Esto se denomina "uso de alias".

### <a name="what-is-aliasing"></a>¿Qué es el uso de alias?
El concepto "uso de alias" hace referencia a los usuarios que tienen diferentes identidades para iniciar sesión en Windows (o su Active Directory) y acceder al correo electrónico.

Esta situación puede darse cuando una empresa emplea un servicio en línea de Microsoft para el inicio de sesión en su directorio, como JohnD@contoso.com, pero los usuarios acceden a sus cuentas de correo electrónico con alias o nombres descriptivos, como John.Doe@contoso.com. Muchos usuarios que administran sus suscripciones a través de Microsoft Business Center podrían experimentar un inicio de sesión incorrecto dado que la dirección de correo electrónico proporcionada (John.Doe@contoso.com) no coincide con la dirección de directorio (JohnD@contoso.com) requerida para la autenticación correcta mediante la opción "Cuenta profesional o educativa".

### <a name="what-options-do-i-have"></a>¿De qué opciones dispongo?
Desde la perspectiva del suscriptor, es importante tratarlo primero con el administrador para conocer la configuración de la identidad de la empresa. Si es necesario, es posible que el administrador tenga que actualizar la configuración de la cuenta desde el portal de administración, o bien que necesite crear una cuenta de Microsoft (MSA) con la dirección de correo electrónico corporativa. Antes de llevar a cabo los pasos para crear una MSA, hable con el administrador con respecto a las directivas o los problemas relacionados con esta acción.

## <a name="resources"></a>Recursos
- Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación de Suscripciones de Visual Studio, consulte [Soporte técnico de Suscripciones](https://aka.ms/vssubscriberhelp) de Visual Studio. 

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
- Obtenga información sobre cómo [vincular cuentas de MSA y AAD](/azure/active-directory/b2b/add-users-administrator) en AAD.
- Obtenga más información sobre la [anonimización](anonymization.md).
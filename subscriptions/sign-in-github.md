---
title: Inicio de sesión en Suscripciones de Visual Studio con la cuenta de GitHub | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/09/2020
ms.topic: conceptual
description: Aprenda a iniciar sesión en las suscripciones de Visual Studio con la cuenta de GitHub.
ms.openlocfilehash: 0dcbe5a908a2d149de7c254ec6ac6f3ec1eb6e72
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005269"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Inicio de sesión en las suscripciones de Visual Studio con la cuenta de GitHub 

Los pasos para iniciar sesión en su suscripción de Visual Studio dependen del tipo de cuenta que esté usando. Por ejemplo, puede que esté usando una cuenta Microsoft (MSA) o una dirección de correo electrónico proporcionada por su empresa o centro educativo. A partir de enero de 2019, también puede usar la cuenta de GitHub para iniciar sesión en algunas suscripciones. 

En este artículo se proporcionan los pasos necesarios para iniciar sesión con la cuenta de GitHub.

## <a name="signing-in-with-your-github-account"></a>Inicio de sesión con la cuenta de GitHub

La compatibilidad de identidad de GitHub permite usar la cuenta existente de GitHub como credencial para una cuenta Microsoft nueva o existente al vincular la cuenta de GitHub con la cuenta Microsoft. 

Cuando se inicia sesión con GitHub, Microsoft comprueba si alguna dirección de correo electrónico asociada a la cuenta de GitHub coincide con una cuenta Microsoft personal o de empresa existente. Si la dirección coincide con la cuenta de empresa, se le pide que inicie sesión en esa cuenta en su lugar. Si la dirección coincide con una cuenta personal, se agrega la cuenta de GitHub como método de inicio de sesión a esa cuenta personal.

Después de vincular las credenciales de cuenta de GitHub y Microsoft, puede usar ese inicio de sesión único en cualquier lugar en que se pueda emplear una cuenta Microsoft personal, como sitios de Azure, aplicaciones de Office y Xbox. Estas cuentas también se pueden usar para inicios de sesión de invitado de Azure Active Directory como una cuenta Microsoft, siempre que la dirección de correo electrónico coincida con la de la invitación.

> [!NOTE]
> La vinculación de una identidad de GitHub a una cuenta Microsoft no proporciona a Microsoft ningún acceso de código. Cuando aplicaciones como Azure DevOps y Visual Studio necesitan acceso a los repositorios de código, se le pide que conceda consentimiento específico para este acceso. 

### <a name="frequently-asked-questions"></a>Preguntas más frecuentes
Las siguientes preguntas más frecuentes tratan cuestiones relacionadas con el uso de las credenciales de cuenta de GitHub para iniciar sesión en suscripciones de Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>P: He olvidado mi contraseña de GitHub.  ¿Cómo puedo acceder a mi cuenta ahora?
R:  Puede recuperar la cuenta de GitHub si va a [Restablecer la contraseña](https://github.com/password_reset). También puede recuperar la cuenta Microsoft vinculada a GitHub si escribe la dirección de correo electrónico de la cuenta de GitHub en [Recupera tu cuenta](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>P: He eliminado mi cuenta de GitHub.  ¿Cómo pudo acceder a mi cuenta Microsoft (MSA) ahora?
R: Si no tiene otras credenciales en la MSA (por ejemplo, una contraseña, una aplicación Authenticator o una clave de seguridad), puede recuperar la cuenta Microsoft mediante la dirección de correo electrónico asociada a ella. Para empezar, vaya a [Recupera tu cuenta](https://account.live.com/password/reset). Tiene que agregar una contraseña a la cuenta para que sepamos cómo va a iniciar sesión más adelante. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>P: No hay ninguna opción "Iniciar sesión con GitHub" en la página de inicio de sesión.  ¿Cómo puedo usar mis credenciales de GitHub para iniciar sesión?
R:  Escriba la dirección de correo electrónico de la cuenta de GitHub que eligió al crear la cuenta Microsoft vinculada a GitHub. Se le busca y envía a GitHub para el inicio de sesión. O bien, si hay un vínculo de opciones de inicio de sesión en la página de inicio de sesión, use el botón **Iniciar sesión con GitHub** que se muestra al hacer clic en ese vínculo. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>P: No puedo iniciar sesión en algunas de mis aplicaciones y productos con GitHub.  ¿Por qué?
R:  No todos los productos de Microsoft pueden acceder a GitHub.com desde su página de inicio de sesión, por ejemplo, las consolas Xbox. En este caso, cuando escribe la dirección de correo electrónico de la cuenta de GitHub vinculada, se le envía un código a esa dirección para poder comprobar que se trata realmente de usted. Sigue iniciando sesión en la misma cuenta, solo que con otro método de inicio de sesión. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>P:  He agregado una contraseña a la cuenta Microsoft que he vinculado a mi cuenta de GitHub.  ¿Eso supone un problema?
R:  No, en absoluto. Esto no cambia la contraseña de GitHub; solo dispone de otra manera de iniciar sesión en la cuenta Microsoft. Cada vez que inicie sesión con la dirección de correo electrónico, se le va a ofrecer la posibilidad de iniciar sesión con la contraseña de la cuenta Microsoft o de ir a GitHub para iniciar sesión. Se recomienda encarecidamente que, en caso de necesitar agregar una contraseña, se asegure de que es diferente de la contraseña de la cuenta de GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>P: Quiero agregar la aplicación Authenticator a la cuenta que he creado mediante GitHub.  ¿Puedo hacerlo?
R:  No hay ningún problema: simplemente descargue la aplicación e inicie sesión con la dirección de correo electrónico. Cuando inicia sesión con la dirección de correo electrónico, se le pide que elija la [aplicación Authenticator](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) o GitHub como credencial.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>P: He habilitado la autenticación en dos fases en las cuentas de GitHub y Microsoft (MSA), pero cuando inicio sesión en mi MSA, todavía se me pide que me autentique dos veces.  ¿Por qué?
R: Debido a las restricciones de seguridad, Microsoft cuenta el inicio de sesión con GitHub como una verificación de un solo factor, aunque tenga habilitada la verificación en dos pasos. Por lo tanto, tiene que volver a autenticarse para la cuenta Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>P:  ¿Cómo puedo saber si mi cuenta Microsoft y mi cuenta de GitHub están vinculadas?
R:  Cada vez que inicia sesión mediante su alias de cuenta (dirección de correo electrónico, número de teléfono, nombre de Skype), se le muestran todos los métodos de inicio de sesión de la cuenta. Si no ve GitHub, aún no lo ha configurado.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>P:  ¿Cómo puedo desvincular mis cuentas de GitHub y Microsoft? 
R:  Vaya a la [pestaña Seguridad](https://account.microsoft.com/security) de account.microsoft.com y haga clic en **Más opciones de seguridad** para desvincular la cuenta de GitHub. Al desvincular la cuenta de GitHub, la quita como método de inicio de sesión y elimina el acceso a los repositorios de GitHub en Visual Studio. Es posible que otros productos de Microsoft hayan solicitado acceso a la cuenta de GitHub por separado, así que quitar el acceso aquí no quita el acceso de todos los productos. Vaya a la página [Permisos de la aplicación](https://github.com/settings/applications) del perfil de GitHub para revocar el consentimiento de las aplicaciones que aparecen en la lista.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>P:  Intento usar mi cuenta de GitHub para iniciar sesión, pero se me indica que ya tengo una identidad de Microsoft que debo usar en su lugar.  ¿Qué sucede?
R:  Si tiene una dirección de correo electrónico de Azure Active Directory en la cuenta de GitHub, esto significa que ya tiene una identidad de Microsoft que puede acceder a Azure y ejecutar canalizaciones de CI con el código de GitHub. El empleo de esa cuenta garantiza que los recursos de Azure y las canalizaciones de compilación permanezcan dentro de los límites organizativos. Pero si está realizando trabajo personal, se recomienda usar una dirección de correo electrónico personal en la cuenta de GitHub para tener siempre acceso a ella. Una vez hecho esto, intente volver a iniciar sesión y seleccione **Usar otra dirección de correo electrónico** cuando se le pida iniciar sesión en la cuenta profesional o educativa. Esto le permite crear una nueva cuenta Microsoft con esa dirección de correo electrónico personal.

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Una vez que haya iniciado sesión correctamente en el portal de suscripciones, se recomienda visitar la página Ventajas en https://my.visualstudio.com/benefits y examinar las excelentes herramientas, los servicios y las ofertas disponibles.
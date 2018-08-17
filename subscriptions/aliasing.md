---
title: Posible error en el inicio de sesión en suscripciones de Visual Studio al utilizar alias | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: Get-Started-Article
description: Puede producirse un error en el inicio de sesión si se utilizan alias o nombres descriptivos
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d05ecb8645b9970b08ad15418a43a5c95f8b2c3c
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637687"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Posible error en el inicio de sesión en suscripciones de Visual Studio al utilizar alias

Según el tipo de cuenta utilizada para iniciar sesión, es posible que las suscripciones disponibles no se muestren correctamente al iniciar sesión en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una posible causa es el uso de "alias" o "nombres descriptivos" en lugar de la identidad de inicio de sesión a la que está asignada la suscripción. Esto se denomina "uso de alias".

## <a name="what-is-aliasing"></a>¿Qué es el uso de alias?

El concepto "uso de alias" hace referencia a los usuarios que tienen diferentes identidades para iniciar sesión en Windows (o su Active Directory) y acceder al correo electrónico.

Esta situación puede darse cuando una empresa emplea un servicio en línea de Microsoft para el inicio de sesión en su directorio, como JohnD@contoso.com, pero los usuarios acceden a sus cuentas de correo electrónico con alias o nombres descriptivos, como John.Doe@contoso.com.  Muchos usuarios que administran sus suscripciones a través de Microsoft Business Center podrían experimentar un inicio de sesión incorrecto dado que la dirección de correo electrónico proporcionada (John.Doe@contoso.com) no coincide con la dirección de directorio (JohnD@contoso.com) requerida para la autenticación correcta mediante la opción "Cuenta profesional o educativa".

## <a name="as-an-administrator-what-options-do-i-have"></a>Como administrador, ¿qué opciones tengo?

Como administrador, dispone de dos opciones para asegurarse de que los suscriptores pueden iniciar sesión correctamente en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- La primera de ellas (la recomendada) es aprovechar la cuenta de directorio como dirección asignada en Microsoft Business Center. Consulte la sección [Asignación de suscriptores a una cuenta de directorio](#assigning-subscribers-to-a-directory-account) de este artículo para obtener más detalles.
- La segunda opción (menos segura) consiste en permitir que los suscriptores asocien su dirección de correo electrónico "profesional o educativa" a una cuenta "personal" (conocida como cuenta Microsoft o MSA). Consulte la sección [Definición de una cuenta profesional o educativa como cuenta personal](#defining-a-work-or-school-account-as-a-personal-account ) de este artículo para obtener más detalles.

> [!NOTE]
> Una vez que su empresa se migre al nuevo [Portal de administración](https://manage.visualstudio.com) de suscripciones de Visual Studio, podrá aprovechar las ventajas de la nueva experiencia de administración que permite especificar tanto las direcciones de correo electrónico como de directorio en el perfil del suscriptor.  Obtenga más información acerca de [la migración](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Como suscriptor, ¿qué opciones tengo?

Desde la perspectiva del suscriptor, es importante tratarlo primero con el administrador para conocer la configuración de la identidad de la empresa.  Si es necesario, el administrador quizás tenga que actualizar la configuración de su cuenta desde el Portal de administración, o puede que necesite crear una cuenta de Microsoft (MSA) utilizando su dirección de correo electrónico corporativo.  Antes de llevar a cabo los pasos para crear una MSA, hable con su administrador con respecto a las directivas o los problemas relacionados con esta acción.  Consulte la sección [Definición de una cuenta profesional o educativa como cuenta personal](#defining-a-work-or-school-account-as-a-personal-account ) de este artículo para obtener más detalles.

## <a name="assigning-subscribers-to-a-directory-account"></a>Asignación de suscriptores a una cuenta de directorio

En todos los casos, el administrador de suscripciones de Microsoft Business Center tendrá que usar la dirección del directorio para los nuevos suscriptores, o actualizar la dirección de correo electrónico para los suscriptores "existentes".  Es importante tener en cuenta que el uso de la dirección de directorio implicará que los nuevos suscriptores no reciban un correo electrónico de bienvenida, y el administrador deberá notificar al suscriptor que se le ha asignado una suscripción.  Después de seguir estos pasos, no dude en utilizar la [plantilla](#notifying-your-subscribers-with-directory-addresses) de correo electrónico para la enviar la notificación a los usuarios y ayudarles en el proceso de inicio de sesión.

### <a name="adding-new-subscribers"></a>Incorporación de nuevos suscriptores

Siga estos pasos para agregar un nuevo suscriptor con una cuenta de directorio.

1. Visite [Microsoft Business Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e inicie sesión.
2. En la página de administración, haga clic en **Suscripciones** y, a continuación, en **Suscripciones de Visual Studio**.

    > [!div class="mx-imgBorder"]
    > ![Menú de suscripciones](_img//vlsc/vlsc-subscriptions.png)


3. Haga clic en el **Número de contrato** asociado a la suscripción de Visual Studio.

    > [!div class="mx-imgBorder"]
    > ![Selección de contrato](_img/vlsc/vlsc-agreement.png)

4. Haga clic en **Asignar suscripción**.
5. Seleccione el **Nivel de suscripción** deseado.
6. Compruebe que tiene suscripciones disponibles para asignar y haga clic en **Siguiente**.
7. Escriba los detalles de suscriptor y la dirección del directorio en el campo Dirección de correo electrónico y haga clic en **Siguiente**.
8. Compruebe la información del suscriptor y haga clic en **Finalizar**.
9. Informe al suscriptor de que la suscripción se ha aprovisionado mediante la siguiente [plantilla](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Actualización de un suscriptor existente

Siga estos pasos para actualizar un suscriptor existente añadiéndole una cuenta de directorio.

1. Visite [Microsoft Business Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e inicie sesión.
2. En la página de administración, haga clic en **Suscripciones** y, a continuación, en **Suscripciones de Visual Studio**.
3. Haga clic en el **Número de contrato** asociado a la suscripción de Visual Studio.
4. Haga clic en la **flecha abajo** en la barra de búsqueda.
5. Busque el suscriptor mediante el campo "Dirección de correo electrónico".
6. En la lista de resultados, haga clic en el **Apellido** del suscriptor.
7. Haga clic en **Editar**.
8. Cambie el campo Dirección de correo electrónico a la dirección de directorio que desee y haga clic en **Guardar**.
9. Informe al suscriptor de que la suscripción se ha aprovisionado mediante la siguiente plantilla de correo electrónico.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Notificación a los suscriptores con direcciones de directorio

Dado que el correo electrónico de bienvenida no llegará correctamente al suscriptor, copie y pegue el siguiente mensaje en un correo electrónico y envíelo al suscriptor. Sustituya las palabras entre % por la información pertinente de cada suscriptor.

----------- Copiar a partir de aquí (Ctrl+C) -----------

Estimado %Nombre del suscriptor%:

Se le ha asignado una suscripción de Visual Studio.  Visite https://my.visualstudio.com e inicie sesión con su dirección %DIRECCIÓN DE DIRECTORIO% para activar la suscripción y poder acceder a ella.

Si tiene problemas, póngase en contacto con el equipo de soporte técnico (https://visualstudio.microsoft.com/subscriptions/support/)).

En la parte inferior de la página, seleccione lo siguiente:
   - Cuentas, Suscripciones y Soporte de facturación
   - En Problema, elija Subscription sign in support (Soporte para inicio de sesión en suscripción).
   - Elija el País correspondiente.
   - Seleccione la opción deseada de Soporte técnico asistido.

----------- Fin de la copia -----------



## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Definición de una cuenta profesional o educativa como cuenta personal

Siga las instrucciones descritas en la sección [Asignación de suscriptores a una cuenta de directorio](#assigning-subscribers-to-a-directory-account) para agregar un nuevo usuario o actualizar la dirección de correo electrónico de un usuario en Microsoft Business Center.  En aquellos casos en que el directorio no reconoce la dirección de correo electrónico, el usuario deberá seguir paso a paso el proceso de creación de una nueva cuenta para definir la dirección de correo electrónico como cuenta personal.  A corto plazo, el equipo de suscripciones de Visual Studio ha concedido una exención a la directiva de identidad que se define a continuación, pero estamos viendo la manera de quitar dicha directiva.

> [!WARNING]
> Microsoft no recomienda combinar la identidad "profesional o educativa" con la identidad "personal".  Esto provoca que la organización pierda la propiedad y el control de la cuenta, y el empleado puede seguir teniendo acceso a determinados productos o servicios incluso después de dejar la empresa.  Consulte esta [entrada de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/) del equipo de Microsoft Identity para obtener información adicional.

### <a name="defining-an-email-address-as-a-personal-account"></a>Definición de una dirección de correo electrónico como una cuenta personal

Una vez que se asigna una suscripción al suscriptor, este recibirá un correo electrónico en el que se le pide que visite [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) para aprovechar las ventajas de la suscripción.  Al intentar iniciar sesión, el inicio de sesión en la suscripción de Visual Studio informará de un error por el cual no se reconoce la cuenta.  Antes de iniciar sesión en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs), pida a los suscriptores que sigan estas instrucciones.  Si es necesario, puede utilizar esta [plantilla](#notifying-your-subscribers-using-personal-accounts) para informar al suscriptor después de que se le haya asignado una suscripción.

1. Vaya a https://my.visualstudio.com y haga clic en **Crear nueva cuenta de Microsoft**.

2. Complete los campos:
    - Escriba la dirección de correo electrónico en la que recibió el correo electrónico de bienvenida en el cuadro Someone@example.com.
    - Cree la contraseña.
    - Elija la configuración de la promoción.
    - Haga clic en **Siguiente**.

3. Complete los pasos de validación y haga clic en **Siguiente**.

4. Es posible que los usuarios nuevos tengan que completar el perfil de Visual Studio.

5. La suscripción y las ventajas ahora deben ser visibles.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Notificación a los suscriptores con cuentas personales

En el escenario descrito anteriormente, el suscriptor recibirá un "correo electrónico de bienvenida", pero debido al uso de alias es posible que no pueda iniciar sesión.  Puede usar el siguiente texto para informar a los suscriptores de los pasos anteriores y recomendar las opciones de soporte técnico si fuera necesario.  Sustituya las palabras entre % por la información pertinente de cada suscriptor.

----------- Copiar a partir de aquí (Ctrl+C) -----------

Estimado %Nombre del suscriptor%:

Se le ha asignado una suscripción de Visual Studio, y es posible que se le haya dirigido a https://my.visualstudio.com para que inicie sesión a partir del correo electrónico de bienvenida.  Si bien este es el sitio web correcto para aprovechar los beneficios, nuestra organización requiere que realice algunos pasos adicionales para tener acceso al sitio.  Siga estas instrucciones para crear una "cuenta Microsoft" asociada a nuestra dirección de correo electrónico corporativo.  Una vez completados estos pasos, usará su dirección de correo electrónico para tener acceso a los beneficios de la suscripción.
1. Visite https://my.visualstudio.com

2. Haga clic en Crear nueva cuenta de Microsoft en el lado derecho.

3. Complete el formulario:
    - Use su dirección de correo electrónico corporativo en el cuadro someone@example.com.
    - Escriba una contraseña.
    - Seleccione sus preferencias promocionales.
    - Haga clic en Siguiente.

4. Complete los pasos de validación de la cuenta.

5. Si fuera necesario, complete el perfil de Visual Studio.

6. Ahora debería ver los beneficios.

Nota: Al visitar https://my.visualstudio.com en el futuro, es posible que se le solicite que seleccione la cuenta que quiere utilizar (por ejemplo, "Cuenta profesional o educativa" o "Cuenta personal").  Después de seguir los pasos anteriores, debe utilizar la opción "Cuenta personal".

Si tiene problemas, póngase en contacto con el equipo de soporte técnico (https://visualstudio.microsoft.com/subscriptions/support/)).

En la parte inferior de la página, seleccione lo siguiente:
   - Cuentas, Suscripciones y Soporte de facturación
   - En Problema, elija Subscription sign in support (Soporte para inicio de sesión en suscripción).
   - Elija el País correspondiente.
   - Seleccione la opción deseada de Soporte técnico asistido.

----------- Fin de la copia -----------

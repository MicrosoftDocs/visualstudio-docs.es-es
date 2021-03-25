---
title: Establecimiento de las preferencias de los contratos en el portal de administración
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/19/2021
ms.topic: conceptual
description: Aprenda a establecer las preferencias de idioma, contactos, nivel de suscripción y demás en el portal de administración.
ms.openlocfilehash: 93a9417a88d07dcc841c6a59a7353b0ffb5e7565
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757625"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Establecimiento de las preferencias de los contratos en el portal de administración
Los superadministradores pueden establecer determinadas preferencias en el portal de administración que se aplicarán globalmente para cada contrato.  Estas preferencias rellenarán automáticamente los detalles de suscripción para los administradores al agregar suscriptores. Solo las pueden modificar de forma global los propios superadministradores.  

## <a name="access-preferences"></a>Preferencias de acceso
Para ver o modificar las preferencias, debe iniciar sesión en el [portal de administración](https://manage.visualstudio.com) con un identificador de inicio de sesión que tenga derechos de superadministrador en el contrato.  

Para establecer las preferencias:
1. Inicie sesión en el portal de administración con un identificador que tenga privilegios de superadministrador.
2. Haga clic en el icono de configuración en el panel izquierdo.
   > [!div class="mx-imgBorder"]
   > ![Botón de preferencias de administración](_img/admin-prefs/admin-prefs-button.png "Haga clic en Administrar administradores y en Agreement Preferences (Preferencias del contrato) para mostrar las preferencias.")

3. Haga clic en **Agreement Preferences** (Preferencias de contratos).
Se abrirá un panel a la izquierda y se mostrarán las preferencias disponibles. 

   > [!div class="mx-imgBorder"]
   > ![Cuadro de diálogo de control flotante con las preferencias de administración](_img/admin-prefs/admin-prefs-flyout.png "Establezca sus preferencias y haga clic en Guardar.")

## <a name="set-your-preferences"></a>Establecimiento de las preferencias
Veamos cada una de las preferencias disponibles y sus efectos. 

### <a name="agreement"></a>Contrato
Si tiene varios contratos de los que es superadministrador, podrá elegir el que le interesa en la lista desplegable a la derecha del panel de configuración expandido.  Las preferencias que establezca se aplicarán solo a ese contrato.  Los administradores individuales pueden invalidar algunas de estas preferencias según cada caso al asignar suscripciones. 

Si solo hay un contrato asociado a la dirección de correo electrónico que usó para iniciar sesión, se mostrará a la derecha del panel de configuración expandido y se deshabilitará la lista desplegable. 

### <a name="contact-email-address"></a>Dirección de correo electrónico de contacto
Esta preferencia proporciona un método para que los suscriptores se pongan en contacto con los administradores mediante el botón **Contact my Admin** (Contacto con el administrador) en la [página de suscripciones](https://my.visualstudio.com/subscriptions) del portal de suscriptor.  Si esta preferencia se deja en blanco, los mensajes del suscriptor se reenviarán a todos los administradores y superadministradores del contrato.  Se recomienda usar un alias de correo electrónico de grupo o un grupo de seguridad para personalizar el público al que está destinado este correo electrónico de contacto. Si lo prefiere, también puede escribir la dirección de correo electrónico de una persona.

> [!NOTE]
> La dirección de correo electrónico que indique aquí NO se proporcionará a los suscriptores.  Cuando un suscriptor envía una solicitud de tipo **Contact my Admin** (Contacto con el administrador) en el portal de suscriptor, el mensaje se reenvía al alias sin exponerlo al suscriptor. 

### <a name="default-subscription-level"></a>Nivel de suscripción predeterminado
Puede usar esta opción para determinar cuál de los niveles de suscripción incluidos en el contrato se selecciona de forma predeterminada cuando se asigna una suscripción a un usuario.  Los administradores pueden cambiar la configuración a cualquier nivel de suscripción en el contrato; evita tener que hacer repetidamente su elección más frecuente. 

### <a name="default-communication-preferences"></a>Preferencias de comunicación predeterminadas
Si establece una configuración regional y un idioma de comunicación predeterminados, puede simplificar el proceso de asignación de suscripciones.  Por ejemplo, si el equipo de desarrollo se encuentra en un país diferente al del equipo de administración, puede establecer las preferencias que mejor se adapten a la ubicación de los suscriptores. Todos los administradores de suscriptores individuales pueden cambiar esta configuración. 

### <a name="default-external-subscribers-setting"></a>Configuración de suscriptores externos predeterminados
Esta preferencia le permite decidir si los administradores pueden agregar suscriptores de fuera del directorio o del inquilino de la organización.  Si se desactiva, no se permitirán los suscriptores externos.  Si se habilita y un administrador intenta agregar un suscriptor externo, se le pedirá que confirme la elección y se le permitirá asignar la suscripción. Los administradores no pueden invalidar esta configuración. 

### <a name="default-downloads-setting"></a>Configuración de descargas predeterminadas
Si se habilita esta opción, que está activada de forma predeterminada, los suscriptores tendrán acceso a las descargas cuando los administradores creen suscripciones.  Aun así, los administradores pueden deshabilitar las descargas por suscripción.  Al deshabilitar el acceso a las descargas también se deshabilita el acceso a las claves de producto.  


## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>P:  ¿Puedo deshabilitar la **dirección de correo electrónico de contacto** para que los suscriptores no puedan ponerse en contacto con los administradores?
R:  No. La característica no se puede deshabilitar, pero puede determinar los administradores con los que ponerse en contacto mediante un grupo de seguridad, un alias de correo electrónico de grupo o una dirección de correo electrónico individual.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>P: Si respondo al correo electrónico de un suscriptor, ¿dispondrá de mi dirección de correo electrónico?
R:  Dado que la respuesta procederá del cliente de correo electrónico que emplee, el mensaje que reciba el suscriptor mostrará la dirección de correo electrónico que use.  Por lo tanto, si responde desde un alias de grupo, el suscriptor verá el alias del grupo.  Si responde desde su propia dirección de correo electrónico, será eso lo que vea.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>P: ¿Dónde puedo encontrar más información sobre la característica **Contact my Admin** (Contacto con el administrador) en el portal de suscriptor?
R:  Consulte nuestro artículo sobre [cómo ponerse en contacto con el administrador](contact-my-admin.md). 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>P: Si no completamos la **dirección de correo electrónico de contacto** y un suscriptor usa la característica **Contact my Admin** (Contacto con el administrador), ¿quién recibe la solicitud?
R:  Si no se establece ninguna dirección de correo electrónico específica en la preferencia **Dirección de correo electrónico de contacto**, todos los administradores del contrato recibirán la solicitud. 

## <a name="resources"></a>Recursos
- [Soporte técnico para suscripciones y administración de Visual Studio](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Determinación del uso máximo](maximum-usage.md)
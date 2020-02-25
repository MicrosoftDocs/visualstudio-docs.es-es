---
title: Posible error en el inicio de sesión en suscripciones de Visual Studio al utilizar alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: Puede producirse un error en el inicio de sesión si se utilizan alias o nombres descriptivos
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276623"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Posible error en el inicio de sesión en suscripciones de Visual Studio al utilizar alias
Según el tipo de cuenta utilizada para iniciar sesión, es posible que las suscripciones disponibles no se muestren correctamente al iniciar sesión en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una posible causa es el uso de "alias" o "nombres descriptivos" en lugar de la identidad de inicio de sesión a la que está asignada la suscripción. Esto se denomina "uso de alias".

## <a name="what-is-aliasing"></a>¿Qué es el uso de alias?
El concepto "uso de alias" hace referencia a los usuarios que tienen diferentes identidades para iniciar sesión en Windows (o su Active Directory) y acceder al correo electrónico.

Esta situación puede darse cuando una empresa emplea un servicio en línea de Microsoft para el inicio de sesión en su directorio, como "olivia@contoso.com", pero los usuarios acceden a sus cuentas de correo electrónico con alias o nombres descriptivos, como "OliviaG@contoso.com". Asegúrese de que sus usuarios inicien sesión mediante "Dirección de correo electrónico de inicio de sesión" tal como se indica en el portal de administración de las suscripciones de Visual Studio en https://manage.visualstudio.com para acceder a sus suscripciones.

## <a name="as-an-administrator-what-options-do-i-have"></a>Como administrador, ¿qué opciones tengo?

En función del tipo de cuenta del suscriptor, vea la solución aplicable a continuación:

### <a name="work-or-school-account-upn-mismatch-issue"></a>Error de coincidencia de UPN de cuenta profesional o educativa

Un error de coincidencia de Nombre principal de usuario (UPN) puede producirse cuando una empresa tiene Active Directory configurado con un UPN que no coincide con la dirección SMTP principal. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Procedimiento para detectar si la dirección de inicio de sesión de un usuario tiene un error de coincidencia de UPN

Haga que el usuario realice los siguientes pasos:

1. Inicie sesión en https://my.visualstudio.com con la dirección de inicio de sesión mencionada en su correo electrónico de asignación de la suscripción.  

    > [!NOTE]
    > Si no tiene su correo electrónico de asignación de la suscripción, puede volver a enviársela desde el portal de administración.  

2. Haga clic en la pestaña **Suscripciones**.
3. Compruebe que la dirección de correo electrónico que se muestra en la parte superior derecha donde dice "Ha iniciado sesión como..." coincida con la dirección de correo electrónico de inicio de sesión del correo electrónico de asignación de la suscripción.  Si no es así, no podrá acceder a las ventajas de su suscripción. 

   > [!div class="mx-imgBorder"]
   > ![Página Suscripciones](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>Procedimiento para corregir el error de coincidencia de UPN

1. Acceda al portal de administración de Visual Studio en https://manage.visualstudio.com. 

2. Encuentre al usuario que tiene el error de coincidencia de UPN.  La característica [Filtro](search-license.md) puede facilitar esta tarea si tiene muchas suscripciones. 

3. Cambie la dirección de correo electrónico de inicio de sesión por el UPN del usuario.

4. Guarde los cambios. 

5. Pida al usuario que cierre sesión en el portal de suscriptores y vuelva a iniciar sesión con el UPN.   

### <a name="personal-account-aliasing-issue"></a>Incidencia sobre alias en una cuenta personal

Las incidencias sobre alias también pueden afectar a las cuentas personales. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Procedimiento para detectar si una cuenta personal tiene una incidencia sobre alias

1. Inicie sesión en https://my.visualstudio.com.

2. Haga clic en la pestaña **Suscripciones** y compruebe la dirección con la que ha iniciado sesión. 

3. Si la dirección de correo electrónico que tiene iniciada la sesión no coincide con la dirección de correo electrónico utilizada para acceder al sitio web, existe un conflicto entre su cuenta y el alias. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Procedimiento para solucionar una incidencia sobre alias en una cuenta personal

La plataforma de suscripciones de Visual Studio da prioridad al alias principal para mostrar los detalles de la suscripción.  Para solucionar la incidencia, debe convertir otro alias de correo electrónico en el alias principal para iniciar sesión. 

1. Vaya a [Administrar el modo de iniciar sesión en Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842796).
2. Inicie sesión en su cuenta Microsoft si se le solicita que lo haga. 
3. En Alias de cuenta, seleccione **Convertir en principal** junto a la dirección de correo electrónico utilizada para asignar la suscripción. 
4. En Alias de cuenta, seleccione Convertir en principal junto a la dirección de correo electrónico utilizada para asignar la suscripción. 
5. Cierre sesión en el portal de suscriptores de Visual Studio (https://my.visualstudio.com) ). 
6. Vuelva a acceder al portal con el nuevo alias principal. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Una experiencia correcta para los usuarios

Como administrador, dispone de dos opciones para asegurarse de que los suscriptores puedan iniciar sesión correctamente en https://my.visualstudio.com. 

- La primera opción (recomendada) es aprovechar la cuenta de directorio como dirección de inicio de sesión en https://manage.visualstudio.com.
- La segunda opción, que es menos segura, consiste en permitir a sus suscriptores iniciar sesión con una dirección de correo electrónico distinta a la del directorio.

Ambas opciones se configuran en el portal de administración completando los pasos siguientes:

1. Inicie sesión en https://manage.visualstudio.com. 

2. Si va a modificar un solo usuario, selecciónelo en la tabla y haga clic con el botón derecho para editarlo. De este modo, se abrirá un panel en el que podrá modificar la dirección de correo electrónico de inicio de sesión.  

3. Realice los cambios necesarios en el campo de dirección de correo electrónico de inicio de sesión. 

4. Haga clic en Guardar y se aplicarán los cambios.  
Si necesita realizar estos cambios para una gran cantidad de usuarios, puede usar la característica de edición en masa. Lea la sección **Edición en masa de varios suscriptores** de nuestro artículo [Edición de suscripciones]](edit-license.md) para obtener más información sobre este proceso.  

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Eliminar suscripciones](delete-license.md)
- [Determinación del uso máximo](maximum-usage.md)

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

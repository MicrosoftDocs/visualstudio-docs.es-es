---
title: Posible error en el inicio de sesión en suscripciones de Visual Studio al utilizar alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: Puede producirse un error en el inicio de sesión si se utilizan alias o nombres descriptivos
ms.openlocfilehash: 1b6c465bc3e850d8582abde200ac9e5bd995e431
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234645"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Posible error en el inicio de sesión en suscripciones de Visual Studio al utilizar alias
Según el tipo de cuenta utilizada para iniciar sesión, es posible que las suscripciones disponibles no se muestren correctamente al iniciar sesión en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Una posible causa es el uso de "alias" o "nombres descriptivos" en lugar de la identidad de inicio de sesión a la que está asignada la suscripción. Esto se denomina "uso de alias".

## <a name="what-is-aliasing"></a>¿Qué es el uso de alias?
El concepto "uso de alias" hace referencia a los usuarios que tienen diferentes identidades para iniciar sesión en Windows (o su Active Directory) y acceder al correo electrónico.

Esta situación puede darse cuando una empresa emplea un servicio en línea de Microsoft para el inicio de sesión en su directorio, como "JohnD@contoso.com", pero los usuarios acceden a sus cuentas de correo electrónico con alias o nombres descriptivos, como "John.Doe@contoso.com". Asegúrese de que sus usuarios usen la "Dirección de correo electrónico de inicio de sesión" tal como se indica en el portal de administración en https://manage.visualstudio.com para acceder a sus suscripciones. 

## <a name="what-are-the-potential-issues"></a>¿Cuáles son los posibles problemas?

En función del tipo de cuenta de suscriptor, pueden encontrarse con uno de estos dos problemas. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Error de coincidencia de UPN de cuenta profesional o educativa 
Un error de coincidencia de nombre principal de usuario (UPN) puede producirse cuando una empresa tiene Active Directory configurado con un UPN que no coincide con la dirección SMTP principal. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Detección de si la dirección de inicio de sesión se ve afectada por una falta de coincidencia de UPN 

1. Inicie sesión en https://my.visualstudio.com/subscriptions con la dirección de inicio de sesión mencionada en su correo electrónico de asignación de la suscripción.

2. Compruebe que la dirección de correo electrónico de inicio de sesión que aparece en la parte superior derecha de la página coincide con la que usó para iniciar sesión.  Si no es así, el UPN no coincide y no podrá ver la suscripción. 

> [!div class="mx-imgBorder"]
> ![Dirección de correo electrónico de inicio de sesión](_img//aliasing/sign-in-email.png "Asegúrese de que la dirección de correo electrónico que se muestra en la parte superior derecha coincide con la que usa para iniciar sesión.")

#### <a name="how-to-fix-a-upn-mismatch"></a>Corrección de un error de coincidencia de UPN

1. Acceda al portal de administración de Visual Studio [https://manage.visualstudio.com](https://manage.visualstudio.com). 

2. Encuentre al suscriptor que tiene el error de coincidencia de UPN. (La característica [Filtro](search-license.md) puede facilitar la búsqueda de un suscriptor).

3. Cambie la dirección de correo electrónico de inicio de sesión por el UPN del suscriptor. 

0. Guarde los cambios. 

0. Informe al suscriptor de que debe cerrar la sesión del portal del suscriptor y volver a acceder a él mediante el UPN. 

### <a name="personal-account-aliasing-issue"></a>Incidencia sobre alias en una cuenta personal

Las cuentas de suscripción personal también pueden experimentar problemas si la dirección de correo electrónico que se usa para iniciar sesión en el Portal de suscripciones de Visual Studio no coincide con la dirección de correo electrónico asociada a la suscripción. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Detección de si la cuenta de suscripción personal se ve afectada por un problema de alias

1. Inicio de sesión en [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Compruebe que la dirección de correo electrónico de inicio de sesión que aparece en la parte superior derecha de la página coincide con la que usó para iniciar sesión.  Si la dirección de correo electrónico que tiene iniciada la sesión no coincide con la dirección de correo electrónico utilizada para acceder al sitio web, existe un conflicto entre su cuenta y el alias.

#### <a name="how-to-fix-an-alias-issue"></a>Corrección de un problema de alias

La plataforma de Visual Studio da prioridad al alias principal para mostrar los detalles de la suscripción. 

1. Vaya a **Administrar el modo de iniciar sesión en Microsoft**. Inicie sesión en su cuenta Microsoft si se le solicita que lo haga. 

2. En Alias de cuenta, seleccione **Convertir en principal** junto a la dirección de correo electrónico utilizada para asignar la suscripción. 

> [!div class="mx-imgBorder"]
> ![Establecimiento de la dirección de correo electrónico principal](_img//aliasing/account-aliases.png "Use el vínculo Convertir en principal para elegir el alias principal de las suscripciones.")

3. Cierre sesión en el portal de suscripciones de Visual Studio (https://my.visualstudio.com) 

4. Vuelva a iniciar sesión con la cuenta usada para asignar la suscripción, que debería estar configurada ahora como alias principal. 

## <a name="preventing-aliasing-issues"></a>Evitación de problemas de alias

Como administrador, dispone de dos opciones para asegurarse de que los suscriptores pueden iniciar sesión correctamente en [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- La primera opción (recomendada) es aprovechar la cuenta de directorio como dirección de inicio de sesión para el portal de suscripciones de Visual Studio en https://my.visualstudio.com.  
- La segunda opción, que es menos segura, consiste en permitir a sus suscriptores iniciar sesión con una dirección de correo electrónico distinta a la del directorio.

Ambas opciones se configuran en el portal de administración completando los pasos siguientes:  
1. Inicie sesión en [https://manage.visualstudio.com](https://manage.visualstudio.com). 

0. Si va a modificar un solo usuario, selecciónelo en la tabla y haga clic con el botón derecho para editarlo. De este modo, se abrirá un panel en el que podrá modificar la dirección de correo electrónico de inicio de sesión. Realice los cambios necesarios en el campo de dirección de correo electrónico de inicio de sesión. Haga clic en Guardar y se aplicarán los cambios.  

0. Si necesita realizar estos cambios para una gran cantidad de usuarios, puede usar la característica de edición en masa. Lea el artículo [Edición en masa de varios suscriptores](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) para obtener más información.

> [!NOTE]
> Tanto para los cambios individuales como para los masivos, los suscriptores recibirán un correo electrónico con instrucciones informando de que su dirección de correo electrónico de inicio de sesión ha cambiado y tendrán que iniciar sesión con la dirección de correo electrónico actualizada. También es importante tener en cuenta que, si el suscriptor activó previamente los beneficios en la otra dirección de inicio de sesión, tendrá que seguir usando la otra dirección de inicio de sesión para acceder a ellos.  

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Determinación del uso máximo](maximum-usage.md)



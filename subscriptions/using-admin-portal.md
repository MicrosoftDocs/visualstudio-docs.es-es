---
title: Introducción al Portal de administración de suscripciones | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Aprenda cómo empezar a administrar las suscripciones de Visual Studio de su organización con el Portal de administración de suscripciones.
ms.openlocfilehash: f3b11a0a0977fff8a6c89f565adffb1cac49e2ad
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605714"
---
# <a name="get-started-with-the-visual-studio-subscriptions-administration-portal"></a>Introducción al Portal de administración de suscripciones de Visual Studio
Tenga esto en cuenta al usar el Portal de administradores de suscripciones de Visual Studio:
- **Para las suscripciones de Visual Studio se concede una licencia por usuario.** Cada suscriptor puede usar el software en todos los equipos necesarios para realizar actividades de desarrollo y pruebas.
- **Asigne solo un nivel de suscripción para cada suscriptor**, el que corresponda a la suscripción de Visual Studio que haya adquirido su organización. Si algún usuario tiene asignados varios niveles de suscripción, modifique su configuración para que solo tenga uno.
- **El nivel de suscripción de un suscriptor tendrá que actualizarse** cuando se actualice la suscripción (después de la adquisición de una licencia de "actualización a edición superior") o se renueve en un nivel inferior.
- **No comparta las suscripciones entre suscriptores.** Las suscripciones se deben asignar a usuarios designados.  No se permite la asignación de suscripciones a equipos.  Debe asignar una suscripción a cualquier usuario que use total o parcialmente las ventajas de la suscripción (software de desarrollo y pruebas, Microsoft Azure, aprendizaje electrónico, etc.).

## <a name="access-to-the-portal"></a>Acceso al portal
Si es el contacto principal o al que se dirigen los avisos en el contrato de la organización, se le proporcionará automáticamente acceso al portal tras configurar el contrato de licencias por volumen. Recibirá un correo electrónico de bienvenida desencadenado por el sistema que le indicará la dirección de correo electrónico que se usará para iniciar sesión en el portal. Cuando haya iniciado sesión, se le configurará automáticamente como superadministrador y podrá empezar a administrar suscripciones y otros administradores. 

## <a name="administrator-roles"></a>Roles de administrador
En el nuevo Portal de administradores de suscripciones de Visual Studio para clientes del programa de licencias por volumen hay dos roles distintos. Estos roles se asemejan al rol de contacto principal y los encargados de los avisos y al rol de administrador de suscripciones en la versión actual de VLSC.

**Superadministradores:** al configurar una organización por primera vez, el contacto principal o el encargado de los avisos es de forma predeterminada el superadministrador. El contacto principal o el que recibe los avisos puede asignar superadministradores o administradores adicionales. Un superadministrador puede agregar y quitar otros administradores, así como suscriptores. Si hay más de dos superadministradores en el sistema, un superadministrador puede eliminarlos a todos menos a los dos últimos por razones de seguridad.

**Administradores:** solo un superadministrador puede configurar administradores. Un administrador puede administrar los suscriptores de los contratos que el superadministrador les asigne.

## <a name="the-subscribers-page"></a>La página Suscriptores
Una vez que haya asignado las suscripciones, la pestaña Suscriptores ofrecerá información detallada sobre los suscriptores, incluida la información siguiente:
- Nombre y apellidos de cada suscriptor.
- Dirección de correo electrónico del usuario.
- Nivel de suscripción que se le ha asignado.
- Fecha de asignación de la suscripción.
- Fecha de expiración de la suscripción.
- Descripción de texto opcional.
- Indicación de si se han habilitado o deshabilitado las descargas para suscriptores.
- País en el que se encuentran.
- Preferencia de idioma para el correo electrónico de comunicación de asignación desde el portal de administración.
- Campo opcional para otra dirección de correo electrónico para las comunicaciones de inicio de sesión.

En el lado izquierdo de esta página puede ver información adicional sobre el número de licencias de suscripción adquiridas, asignadas y todavía disponibles en su organización para cada contrato.
> [!div class="mx-imgBorder"]
> ![Página Suscriptores del Portal de administradores de suscripciones de Visual Studio](_img/using-admin-portal/subscribers-page.png)

## <a name="the-details-page"></a>La página Detalles
Para obtener más información sobre el contrato que está consultando, seleccione la pestaña Detalles. En ella se muestra el estado del contrato, la cuenta de compra, los detalles de la organización, los superadministradores y otra información pertinente.
> [!div class="mx-imgBorder"]
> ![Página Detalles del Portal de administradores de suscripciones de Visual Studio](_img/using-admin-portal/details-page.png)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre las responsabilidades de los administradores:
- [Introducción a las responsabilidades del administrador](admin-responsibilities.md)
- [Inventario de entorno de preproducción](admin-inventory.md)
- [Administración de equipos grandes y contratistas externos](manage-teams.md)
- [Seguimiento de la asignación de usuarios y tramitación de pedidos](assignments-orders.md)
- Emplee [Uso máximo](maximum-usage.md) para realizar el seguimiento de los compromisos de compra

---
title: Eliminación de asignaciones de suscripciones de Visual Studio en el Portal de administración de Suscripciones | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 03/21/2021
ms.topic: how-to
description: Obtenga información sobre la forma en que los administradores pueden eliminar asignaciones de suscripciones en el Portal de administración de Suscripciones de Visual Studio.
ms.openlocfilehash: d0ce93855cf56dab5e1a333e41e24ac2a368a540
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776938"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Eliminación de asignaciones de suscripciones de Visual Studio
Si un suscriptor ya no necesita una suscripción de Visual Studio (por ejemplo, al dejar la empresa), o bien completa un proyecto o cambia a una nueva función, puede quitársela y asignársela a otra persona. Tenga en cuenta que al reasignar una suscripción, no todas las ventajas del suscriptor se restablecerán.  El nuevo usuario podrá solicitar cualquier clave no solicitada y ver las claves solicitadas previamente, pero los límites de solicitud **no** se restablecen.  Para las organizaciones que tengan Contratos Enterprise (EA), se restablecerá cualquier ventaja que el usuario original haya usado, como el aprendizaje de Pluralsight. 
> [!Important]
> Las suscripciones solo se pueden asignar a usuarios distintos si han transcurrido un mínimo de 90 días desde la última vez que se asignó la suscripción.  Por ejemplo, si se asignó una suscripción a un suscriptor el 1 de junio, no se podrá reasignar a otro hasta el 30 de agosto. 

Vea este vídeo o siga leyendo para saber cómo eliminar asignaciones.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Eliminación de una asignación de suscripción
1. Haga clic en el nombre del suscriptor que desea quitar. Para seleccionar varios suscriptores para su eliminación, puede hacer clic en el círculo situado a la izquierda del nombre del suscriptor para seleccionar cada uno de ellos.  También puede mantener presionada la tecla **CTRL** y hacer clic en cada suscriptor que desee quitar. Para quitar un intervalo de suscriptores, haga clic en el primero, presione la tecla **Mayús** y haga clic en el último.  Presione **CTRL+A** para seleccionar y quitar todos los suscriptores. En este ejemplo, se eliminarán tres suscriptores: Amber, Kai y Madison. 
2. Para eliminar los suscriptores seleccionados, haga clic en **Eliminar**.
3. Cuando aparezca el mensaje que le pide que confirme la eliminación, haga clic en **Aceptar**.
   > [!div class="mx-imgBorder"]
   > ![Eliminar suscriptores](_img/delete-license/delete-subscribers.png "Elija los usuarios que desea eliminar y haga clic en Eliminar. Puede usar las teclas CTRL y Mayús para seleccionar varios suscriptores.")

   > [!NOTE]
   > La eliminación masiva con una plantilla no está disponible. 
   >
   > Si agregó asignaciones de suscripciones a través de los grupos de seguridad de Azure Active Directory, la actualización de la eliminación en el portal de administradores puede tardar hasta 24 horas.  Consulte [nuestro artículo](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) para más información sobre cómo usar los grupos de Azure Active Directory para administrar las suscripciones. 

## <a name="resources"></a>Recursos
- [Soporte de la suscripción de Visual Studio](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
- ¿Necesita cambiar una suscripción sin eliminarla?  Aprenda a [editar suscripciones](edit-license.md).
- Si necesita ayuda para encontrar una suscripción determinada, consulte [Búsqueda de suscripciones](search-license.md).
- ¿Necesita crear una lista de todas las suscripciones?  Consulte [Exportar suscripciones](exporting-subscriptions.md).
---
title: Eliminación de asignaciones en el Portal de administración de suscripciones | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 09/21/2020
ms.topic: how-to
description: Obtenga información sobre la forma en que los administradores pueden eliminar asignaciones de suscripciones en el Portal de administración de Suscripciones de Visual Studio.
ms.openlocfilehash: 0ce0235d75946f46d39c78084121ce295067d74e
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022272"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Eliminación de asignaciones de suscripciones de Visual Studio
Cuando un suscriptor ya no requiera una suscripción de Visual Studio, por ejemplo, cuando deje la empresa, complete un proyecto o cambie a una nueva función, puede quitar su suscripción y asignarla a otra persona. Tenga en cuenta que al reasignar una suscripción, no todas las ventajas del suscriptor se restablecerán.  El nuevo usuario podrá solicitar cualquier clave no solicitada y ver las claves solicitadas previamente, pero los límites de solicitud **no** se restablecen.  Para las organizaciones que tengan Contratos Enterprise (EA), se restablecerá cualquier ventaja que el usuario original haya usado, como el aprendizaje de Pluralsight. 

Vea este vídeo o siga leyendo para saber cómo eliminar asignaciones.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Eliminación de una asignación de suscripción
1. Haga clic en el nombre del suscriptor que desea quitar. Para seleccionar varios suscriptores para su eliminación, puede hacer clic en el círculo situado a la izquierda del nombre del suscriptor para seleccionar cada uno de ellos.  También puede mantener presionada la tecla **CTRL** y hacer clic en cada suscriptor que desee quitar. Para quitar un intervalo de suscriptores, haga clic en el primero, presione la tecla **Mayús** y haga clic en el último.  Presione **CTRL+A** para seleccionar y quitar todos los suscriptores. En este ejemplo, se eliminarán tres suscriptores: Amber, Kai y Madison. 
2. Para eliminar los suscriptores seleccionados, haga clic en **Eliminar**.
3. Cuando aparezca el mensaje que le pide que confirme la eliminación, haga clic en **Aceptar**.
   > [!div class="mx-imgBorder"]
   > ![Eliminar suscriptores](_img/delete-license/delete-subscribers.png "Elija los usuarios que desea eliminar y haga clic en Eliminar. Puede usar las teclas CTRL y Mayús para seleccionar varios suscriptores.")

   > [!NOTE]
   > La eliminación masiva con una plantilla no está disponible. Para las organizaciones que administran las asignaciones de suscripciones a través de grupos de seguridad de Azure Active Directory, consulte [nuestro artículo](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) para obtener más información sobre cómo se realizan las eliminaciones.  

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
- ¿Necesita cambiar una suscripción sin eliminarla?  Aprenda a [editar suscripciones](edit-license.md).
- Si necesita ayuda para encontrar una suscripción determinada, consulte [Búsqueda de suscripciones](search-license.md).
- ¿Necesita crear una lista de todas las suscripciones?  Consulte [Exportar suscripciones](exporting-subscriptions.md).
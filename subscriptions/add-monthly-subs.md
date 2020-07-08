---
title: Incorporación de suscripciones mensuales nuevas de Visual Studio al Portal de administración de suscripciones | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: how-to
description: Obtenga información sobre cómo agregar suscripciones mensuales de Visual Studio recién compradas al Portal de administración de suscripciones
ms.openlocfilehash: 778a3adbc9ca2117b0328a10d52904921bd0b80c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904693"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Incorporación de suscripciones mensuales nuevas a Visual Studio en el Portal de administración de suscripciones
Al comprar suscripciones mensuales nuevas de Visual Studio con una suscripción de Azure, es posible que deba agregarlas al Portal de administración de suscripciones para asignarlas a los usuarios.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>¿Cómo saber si necesito agregar mis suscripciones?
Los pasos para agregar suscripciones mensuales dependen de qué tipos de suscripciones tenga su organización y de si es un administrador nuevo.
- Si es un administrador nuevo, buscaremos suscripciones de Azure en las que tenga derechos de administrador de acceso de usuario al iniciar sesión por primera vez en el Portal de administración de suscripciones.  Si encontramos suscripciones mensuales, las agregaremos automáticamente. 
- Si agregó o administró suscripciones mensuales anteriormente, buscaremos suscripciones mensuales nuevas cada vez que inicie sesión. 
- Si ya es un administrador de suscripciones adquiridas a través de licencias por volumen, pero no ha agregado ni administrado previamente suscripciones mensuales, deberá agregarlas con los pasos que se indican a continuación.

## <a name="how-to-add-monthly-subscriptions"></a>Incorporación de suscripciones mensuales
1. Inicie sesión en el Portal de administración de suscripciones en <https://manage.visualstudio.com>
1. En la pestaña **Administrar suscriptores**, elija el menú desplegable **Nuevo acuerdo** 
1. Elija **New monthly subscriptions** (Suscripciones mensuales nuevas) en el menú desplegable
   > [!div class="mx-imgBorder"]
   > ![Menú desplegable para agregar suscripciones mensuales nuevas](_img/add-monthly-subs/add-subs-drop-down.png)
1. El sistema buscará las suscripciones de Azure en las que tenga derechos de administrador de acceso de usuario e importará las suscripciones de Visual Studio adquiridas con esas suscripciones de Azure.
1. Si no se encuentran suscripciones de Azure en las que tenga derechos de administrador de acceso de usuario o si se encontraron de Azure, pero no suscripciones de Visual Studio, recibirá el mensaje siguiente:
   > [!div class="mx-imgBorder"]
   > ![No se encontraron suscripciones mensuales nuevas](_img/add-monthly-subs/no-subs-found.png)
1. Si se encuentran suscripciones mensuales nuevas, recibirá un mensaje de confirmación.
   > [!div class="mx-imgBorder"]
   > ![Mensaje de confirmación de suscripciones agregadas](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>Aspectos que debe tener en cuenta
- La opción de agregar suscripciones mensuales nuevas solo estará disponible la primera vez que las compre.  Una vez que haya agregado las suscripciones mensuales, buscaremos suscripciones nuevas cada vez que inicie sesión en el portal. 
- Cuando se encuentran suscripciones nuevas, puede ver que ya están asignadas a los suscriptores.  Esto se debe a que hay otros administradores con acceso a la suscripción de Azure y ya han asignado las suscripciones nuevas de Visual Studio a los usuarios.  Ahora que también agregó esas suscripciones a su portal, puede administrarlas. 

## <a name="next-steps"></a>Pasos siguientes
Ahora que agregó suscripciones, está listo para asignarlas a los usuarios.  Existen varias maneras de hacerlo:
- [Asignación individual de suscripciones](assign-license.md)
- [Asignación de suscripciones a varios usuarios](assign-license-bulk.md)
- [Asignación de suscripciones específicas a usuarios específicos](assign-guid.md)

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)

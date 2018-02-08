---
title: "Reenvío de correos electrónicos de asignación de suscripción desde Microsoft Business Center | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 12/29/2017
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to a subscriber from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 7162435044a578a94249774305f2c6b8b6438219
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-vlsc"></a>Reenvío de correos electrónicos de asignación de suscripción desde Microsoft Business Center

Cuando una suscripción se ha asignado a un suscriptor en Microsoft Business Center y el suscriptor solicita el reenvío del correo electrónico de asignación, puede modificar la información de correo electrónico del suscriptor y, a continuación, cambiarla de nuevo a la dirección original para atender la petición. De este modo se desencadenará el reenvío automático del correo electrónico de asignación.

Siga estas instrucciones para volver a enviar el correo electrónico de asignación:


1. Visite Microsoft Business Center e inicie sesión.
2. En la página de administración, haga clic en **Suscripciones** y, a continuación, en **Suscripciones de Visual Studio**.
3. Haga clic en el **Número de contrato** asociado a la suscripción de Visual Studio.
4. Haga clic en la flecha abajo en la barra de **búsqueda**.  
5. Busque el suscriptor mediante el campo Dirección de correo electrónico.
6. En la lista de resultados, haga clic en el **Apellido** del suscriptor.
7. Haga clic en **Editar**.
8. Realice una modificación en la suscripción. El cambio que realice no es pertinente: basta con que haya un cambio.  Por ejemplo, quite un carácter de la dirección de correo electrónico del suscriptor (quite la "m" de .com). Haga clic en el botón **Guardar**.
9. Una vez que se guarde la información, haga clic nuevamente en el botón **Editar** y corrija el cambio que haya hecho en la dirección de correo electrónico. Haga clic en **Guardar**.
   
Esto hará que Microsoft Business Center reconozca que hubo cambios en la suscripción y vuelva a enviar el correo electrónico de asignación al correo electrónico que figura en el portal. 

> [!NOTE]
> - Las suscripciones recién asignadas generarán automáticamente el correo electrónico de asignación. Los pasos anteriores solo son necesarios cuando un usuario solicita una nueva notificación de correo electrónico de asignación o si la notificación no se ha enviado por cualquier motivo.
> - Este procedimiento no es necesario para volver a enviar correos electrónico de asignación para las suscripciones asignadas a través de https://manage.visualstudio.com.  Para reenviar mensajes de correo electrónico de asignación a los suscriptores del portal, simplemente seleccione los suscriptores y haga clic en el botón **Reenviar** situado en la parte superior de la lista de suscriptores.  
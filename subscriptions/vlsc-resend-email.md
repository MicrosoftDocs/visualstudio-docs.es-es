---
title: "Suscripciones de Visual Studio: reenvío de correos electrónicos de asignación desde Microsoft Business Center"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/16/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>Cómo volver a enviar correos electrónicos de asignación de suscripción desde Microsoft Business Center

En ocasiones, un suscriptor al que se le ha asignado una suscripción pedirá a un administrador que le vuelva a enviar su correo electrónico de notificación de asignación de suscripción.  En el nuevo Portal de administración de suscripciones (https://manage.visualstudio.com), este es un proceso sencillo.  Sin embargo, si su organización sigue usando Microsoft Business Center, no existe ninguna característica específica para reenviar automáticamente el correo electrónico de notificación.  

Para reenviar el correo de notificación de asignación desde Microsoft Business Center, un administrador debe utilizar la siguiente solución alternativa:

## <a name="resending-the-assignment-email"></a>Reenvío del correo electrónico de asignación:

Para que Microsoft Business Center genere una nueva notificación, es necesario modificar la información de correo electrónico del suscriptor una vez y, a continuación, cambiarla de nuevo al correo electrónico original en la misma transacción. De este modo, Microsoft Business Center reaccionará como si se hubiese creado una nueva asignación y volverá a enviar el correo electrónico de asignación.

1.  Visite [Microsoft Business Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e inicie sesión.
2.  Haga clic en la pestaña **Suscripciones** y elija **Suscripciones de Visual Studio**.
3.  Haga clic en el **Número de contrato** asociado a la suscripción de Visual Studio.
4.  Haga clic en la flecha abajo en la barra de búsqueda. 
5.  Busque el suscriptor mediante el campo **Dirección de correo electrónico**.
6.  Busque el suscriptor en los resultados de la búsqueda y haga clic en el apellido. 
7.  Haga clic en **Editar**.
8.  Realice una modificación en la suscripción. Por ejemplo, quite un carácter de la dirección de correo electrónico del suscriptor. Haga clic en el botón **Guardar**.
9.  Una vez que se haya guardado la información, haga clic en **Editar** de nuevo, revierta el cambio que acaba de realizar y haga clic en **Guardar**.  

Esto hará que la suscripción se trate como una nueva asignación y se volverá a enviar el correo electrónico de notificación de asignación al suscriptor.  
---
title: "Reenvío de correos electrónicos de asignación de suscripción desde Manage.visualstudio. com o VLSC | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 2/13/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to subscribers from manage.visualstudio.com or VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 0ba7d6e36c25ced78b0c6b25688e5eb5b26eb04a
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-resend-subscription-assignment-emails"></a>Reenvío de correos electrónicos de asignación de suscripción:

Los pasos necesarios para reenviar un correo electrónico de asignación dependen del portal que esté utilizando para administrar sus suscripciones. 

## <a name="resending-assignment-emails-from-within-managevisualstudiocom"></a>Reenvío de correos electrónicos de asignación desde manage.visualstudio.com

El proceso para reenviar correos electrónicos de asignación desde el portal de manage.visualstudio.com es muy sencillo:

1. Visite el portal [manage.visualstudio.com](https://manage.visualstudio.com) e inicie sesión. 
2. Utilice la pestaña **Filtro** para buscar el suscriptor al que desea reenviar el correo electrónico de asignación. (Para más información sobre el filtrado, consulte [Búsqueda de una suscripción](/visualstudio/subscriptions/search-license)).
3. Haga clic en los suscriptores.  Puede usar Ctrl + clic o Mayús + clic para seleccionar varios suscriptores.
4. Haga clic en **Reenviar** en la parte superior de los resultados de búsqueda.  

## <a name="resending-assignment-emails-from-within-vlsc"></a>Reenvío de correos electrónicos de asignación desde VLSC
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

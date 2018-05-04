---
title: Cómo desbloquear Visual Studio
ms.date: 07/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a85e2d8f057a84b56553e8592b3f6a5e390690a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-unlock-visual-studio"></a>Cómo desbloquear Visual Studio

Visual Studio se puede probar de forma gratuita durante 30 días. Al iniciar sesión en el IDE, extiende el período de prueba a 90 días. Para seguir usando Visual Studio, desbloquee el IDE mediante:

- una suscripción en línea;

- una clave de producto.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Para desbloquear Visual Studio con una suscripción en línea

Para desbloquear Visual Studio mediante una suscripción a Visual Studio Visual Studio Team Service o a MSDN que esté asociada con una cuenta Microsoft o con una cuenta profesional o educativa:

1. Haga clic en el botón **Iniciar sesión** en la esquina superior derecha del IDE (o vaya a **Archivo** > **Configuración de la cuenta** para abrir el cuadro de diálogo **Configuración de la cuenta** y haga clic en el botón **Iniciar sesión**).

1. Escriba las credenciales de la cuenta (Microsoft, profesional o educativa). Visual Studio busca una suscripción a Visual Studio o a Visual Studio Team Services que esté asociada con su cuenta.

> [!IMPORTANT]
> Visual Studio busca automáticamente las suscripciones en línea asociadas al conectarse a una cuenta de Visual Studio Team Services desde la ventana de herramientas de **Team Explorer**. Al conectarse a una cuenta de Visual Studio Team Services, puede iniciar sesión con la cuenta Microsoft o con la cuenta profesional o educativa. Si existe una suscripción en línea para esa cuenta de usuario, Visual Studio desbloqueará automáticamente el IDE.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Para desbloquear Visual Studio con una clave de producto

1. Seleccione **Archivo** > **Configuración de la cuenta** para abrir el cuadro de diálogo **Configuración de la cuenta** y haga clic en el vínculo **Licencia con una clave de producto**.

Escriba la clave de producto en el espacio para ello.

> [!TIP]
> Las versiones preliminares de Visual Studio no tienen claves de producto. Para poder usar esas versiones preliminares, debe iniciar sesión en el IDE.

## <a name="address-license-problem-states"></a>Resolver problemas de estado de licencia

### <a name="update-stale-licenses"></a>Actualizar licencias obsoletas

 Es posible que haya visto el mensaje siguiente donde se indica que su licencia de Visual Studio se está quedando obsoleta: "Su licencia ha quedado obsoleta y debe actualizarse".

 ![Mensaje de licencia obsoleta de Visual Studio](../ide/media/vs2017_stale-license.png)

 Este mensaje indica que, aunque es posible que la licencia aún sea válida, el token de licencia que usa Visual Studio para mantener actualizada la suscripción no se ha actualizado y ha quedado obsoleto debido a uno de los siguientes motivos:

- No se ha usado Visual Studio o no ha habido conexión a Internet durante un período prolongado de tiempo.
- Se cerró la sesión de Visual Studio.

Antes de que el token de licencia quede obsoleto, Visual Studio muestra un mensaje de advertencia donde se le pide que vuelva a escribir sus credenciales.

Si no vuelve a escribirlas, el token empieza a quedar obsoleto y en el cuadro de diálogo **Configuración de la cuenta** se le indica cuántos días quedan antes de que el token expire por completo. Si el token expira, habrá que introducir de nuevo las credenciales de esta cuenta o licencia con el otro método anterior para poder continuar usando Visual Studio.

> [!Important]
> Si trabaja con Visual Studio durante largos períodos en entornos con poco o ningún acceso a Internet, use una clave de producto para desbloquear Visual Studio con el fin de evitar la interrupción.

### <a name="update-expired-licenses"></a>Actualizar licencias caducadas

 Si su suscripción ha expirado por completo y ya no tiene derechos de acceso a Visual Studio, debe renovar la suscripción o agregar otra cuenta que tenga una suscripción. Para obtener más información sobre su licencia actual, vaya a **Archivo** > **Configuración de la cuenta** y vea la información de licencia que aparece en el lado derecho del cuadro de diálogo. Si tiene otra suscripción asociada a una cuenta diferente, agregue esa cuenta a la lista **Todas las cuentas**, en el lado izquierdo del cuadro de diálogo. Para ello, seleccione el vínculo **Agregar una cuenta**.

## <a name="see-also"></a>Vea también

* [Inicio de sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)
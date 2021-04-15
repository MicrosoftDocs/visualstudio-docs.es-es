---
title: Ampliar una versión de prueba o actualizar una licencia
description: Obtenga información sobre cómo ampliar una evaluación gratuita de Visual Studio, usar una suscripción en línea o una clave de producto para desbloquear Visual Studio y actualizar una licencia obsoleta o expirada.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: b78db14b149b094550ce025ab3750742401fddbe
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295473"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Ampliar una versión de prueba o actualizar una licencia

Puede utilizar una evaluación gratuita de [Visual Studio Professional o Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) durante 30 días. Y, si inicia sesión, puede ampliar el período de prueba a 90 días. (Visual Studio Community es gratuito sin un período de prueba. Sin embargo, debe [iniciar sesión](signing-in-to-visual-studio.md) periódicamente para mantener la [licencia actualizada](#update-a-stale-license)).

Para seguir usando Visual Studio una vez finalizado el período de prueba, desbloquéelo con una [suscripción en línea](#use-an-online-subscription) o una [clave de producto](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Uso de una suscripción en línea

1. Haga clic en el botón **Iniciar sesión** en la esquina superior derecha del IDE (o vaya a **Archivo** > **Configuración de la cuenta** para abrir el cuadro de diálogo **Configuración de la cuenta** y, luego, seleccione el botón **Iniciar sesión**).

1. Escriba las credenciales de la cuenta (Microsoft, profesional o educativa). Visual Studio busca una suscripción a Visual Studio o una organización de Azure DevOps que esté asociada con su cuenta.

> [!IMPORTANT]
> Visual Studio busca automáticamente las suscripciones en línea asociadas al conectarse a una organización de Azure DevOps desde la ventana de herramientas de **Team Explorer**. Al conectarse a una organización de Azure DevOps, puede iniciar sesión con la cuenta de Microsoft o con la cuenta profesional o educativa. Si existe una suscripción en línea para esa cuenta de usuario, Visual Studio desbloqueará automáticamente el IDE.

Para obtener más información acerca de las suscripciones de Visual Studio y cómo funcionan, consulte la página de [preguntas más frecuentes sobre el soporte técnico de suscripciones](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="enter-a-product-key"></a>Especificación de una clave de producto

1. Seleccione **Archivo** > **Configuración de la cuenta** para abrir el cuadro de diálogo **Configuración de la cuenta** y haga clic en el vínculo **Licencia con una clave de producto**.

1. Escriba la clave de producto en el espacio para ello.

> [!TIP]
> Las versiones preliminares de Visual Studio no tienen claves de producto. Para poder usar esas versiones preliminares, debe iniciar sesión en el IDE.

Para obtener más información sobre las claves de producto de Visual Studio para Visual Studio y cómo obtenerlas, consulte la página [Uso de claves de producto en suscripciones de Visual Studio](/visualstudio/subscriptions/product-keys).

## <a name="update-a-stale-license"></a>Actualización de licencias obsoletas

Es posible que vea un mensaje en Visual Studio que indica que su licencia ha quedado obsoleta y debe actualizarse.

![Mensaje de licencia obsoleta de Visual Studio](../ide/media/vs2017_stale-license.png)

Este mensaje indica que, aunque es posible que la licencia aún sea válida, el token de licencia que usa Visual Studio para mantener actualizada la suscripción no se ha actualizado. Visual Studio informa de que la licencia se ha quedado obsoleta debido a uno de los siguientes motivos:

* No ha usado Visual Studio o no se ha conectado a Internet durante un período de tiempo prolongado.
* Se cerró la sesión de Visual Studio.

Antes de que el token de licencia quede obsoleto, Visual Studio muestra un mensaje de advertencia donde se le pide que vuelva a escribir sus credenciales.

Si no vuelve a escribirlas, el token empieza a quedar obsoleto y en el cuadro de diálogo **Configuración de la cuenta** se le indica cuántos días quedan antes de que el token expire. Una vez que el token expire, deberá volver a escribir las credenciales de la cuenta para seguir usando Visual Studio.

> [!Important]
> Si trabaja con Visual Studio durante largos períodos en entornos con poco o ningún acceso a Internet, use una clave de producto para desbloquear Visual Studio con el fin de evitar la interrupción.

## <a name="update-an-expired-license"></a>Actualización de una licencia caducada

Si su suscripción ha expirado y ya no tiene derechos de acceso a Visual Studio, debe renovar la suscripción o agregar otra cuenta que tenga una suscripción. Para obtener más información sobre su licencia actual, vaya a **Archivo** > **Configuración de la cuenta** y vea la información de licencia que aparece en el lado derecho del cuadro de diálogo. Si tiene otra suscripción asociada a una cuenta diferente, agregue esa cuenta a la lista **Todas las cuentas**, en el lado izquierdo del cuadro de diálogo. Para ello, seleccione el vínculo **Agregar una cuenta**.

## <a name="get-support"></a>Obtención de soporte técnico

En ocasiones, algo no sale según lo previsto. Si experimenta un problema, estas son algunas opciones de soporte técnico:

* Informe de los problemas del producto mediante la herramienta [Notificar un problema](how-to-report-a-problem-with-visual-studio.md).
* Encuentre respuestas a preguntas acerca de las suscripciones, las cuentas y la facturación en las [preguntas más frecuentes sobre el soporte técnico de suscripciones](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Vea también

* [Inicio de sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Comparar las ediciones de Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Más información sobre las suscripciones de Visual Studio](/visualstudio/subscriptions/)

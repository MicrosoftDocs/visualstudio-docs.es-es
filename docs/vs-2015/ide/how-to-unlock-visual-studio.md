---
title: Desbloqueo de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a71a045661c48fd36733ecd8d2266470667a5c35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670593"
---
# <a name="how-to-unlock-visual-studio"></a>Cómo desbloquear Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio se puede probar de forma gratuita durante 30 días. Si desea extender el período de prueba a 90 días, puede hacerlo al iniciar sesión en el IDE. Para seguir usando Visual Studio, desbloquee el IDE mediante

1. una suscripción en línea;

2. una clave de producto.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Para desbloquear Visual Studio con una suscripción en línea
 Para desbloquear Visual Studio mediante una suscripción en línea a Visual Studio o a MSDN que esté asociada con una cuenta Microsoft o con una cuenta profesional o educativa:

1. Haga clic en el botón “Iniciar sesión” en la esquina superior derecha del IDE (o vaya a Archivo > Configuración de la cuenta para abrir el cuadro de diálogo Configuración de la cuenta y haga clic en el botón “Iniciar sesión”).

2. Escriba las credenciales de la cuenta (Microsoft, profesional o educativa). Visual Studio encontrará la suscripción a MSDN o a Visual Studio Team Services que está asociada con su cuenta.

> [!IMPORTANT]
> Visual Studio busca automáticamente las suscripciones en línea asociadas al conectarse a una cuenta de Visual Studio Team Services desde la ventana de herramientas de Team Explorer. Al conectarse a una cuenta de Visual Studio Team Services, puede iniciar sesión con la cuenta Microsoft o con la cuenta profesional o educativa. Si existe una suscripción en línea para esa cuenta de usuario, Visual Studio desbloqueará automáticamente el IDE.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Para desbloquear Visual Studio con una clave de producto

1. Seleccione **Archivo > Configuración de la cuenta** para abrir el cuadro de diálogo Configuración de la cuenta y haga clic en el vínculo "**Licencia con una clave de producto**".

2. Escriba la clave de producto en el espacio para ello.

> [!TIP]
> Las versiones preliminares de Visual Studio no tienen claves de producto. Para poder usar esas versiones preliminares, debe iniciar sesión en el IDE.

## <a name="addressing-license-problem-states"></a>Resolución de problemas de estado de licencia

### <a name="updating-stale-licenses"></a>Actualizar licencias obsoletas
 Es posible que haya visto el mensaje siguiente donde se indica que su licencia de Visual Studio se está quedando obsoleta.

 ![Cuadro de diálogo de información de usuario de Visual Studio](../ide/media/vs2013-userinfo.png "VS2013_UserInfo")

 Este mensaje indica que, aunque es posible que la licencia aún sea válida, el token de licencia que usa Visual Studio para mantener actualizada la suscripción no se ha actualizado y ha quedado obsoleto debido a uno de los siguientes motivos:

1. No se usó Visual Studio o no hubo conexión a Internet durante un período prolongado de tiempo.

2. Se cerró la sesión de Visual Studio.

   Antes de que el token de licencia quede obsoleto, Visual Studio mostrará un mensaje de advertencia donde se le pedirá que vuelva a introducir sus credenciales.

   Si no vuelve a introducir sus credenciales, el token irá quedando poco a poco obsoleto. Cuando esto sucede, el cuadro de diálogo Configuración de la cuenta muestra el número de días que quedan antes de la expiración definitiva del token. Si el token expira, habrá que introducir de nuevo las credenciales de esta cuenta o licencia con el otro método anterior para poder continuar usando Visual Studio.

> [!IMPORTANT]
> Si trabaja con Visual Studio durante largos períodos en entornos con poco o ningún acceso a Internet, use una clave de producto para desbloquear Visual Studio con el fin de evitar la interrupción.

### <a name="updating-expired-licenses"></a>Actualizar licencias caducadas
 Si su suscripción ha expirado por completo y ya no tiene derechos de acceso a Visual Studio, debe:

1. Renovar su suscripción. Para obtener más información sobre su licencia actual, vaya a Archivo > Configuración de la cuenta y vea la información de licencia que aparece en el lado derecho del cuadro de diálogo.

2. Si tiene otra suscripción asociada a una cuenta diferente, agregue esa cuenta a la lista Todas las cuentas, en el lado izquierdo del cuadro de diálogo Archivo > Configuración de la cuenta. Para ello, haga clic en el vínculo “Agregar una cuenta...” que se mostrará.

## <a name="see-also"></a>Consulte también
 [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)

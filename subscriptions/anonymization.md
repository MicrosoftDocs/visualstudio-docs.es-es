---
title: Anonimización de datos de suscriptor de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: Obtenga información sobre cómo se anonimizan los datos del suscriptor cuando se pierde el acceso a las suscripciones.
searchscope: VS Subscription
ms.openlocfilehash: a4249aa2520df6e9c1870fec121de2fdb2135308
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842551"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonimización de información de suscriptor de Visual Studio

Cuando se produce un evento que bloquea el uso que realiza un suscriptor de una suscripción, como la expiración de una suscripción o la eliminación de la cuenta de inicio de sesión del suscriptor, la información personal del usuario como su nombre y la cuenta de inicio de sesión se desordenan para volverlos inutilizables.  Esto se hace para proteger la información personal del suscriptor.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>¿Cuando se produce la anonimización?

Los eventos que inutilizan una suscripción para un suscriptor desencadenarán la anonimización.  La rapidez con la que se produce la anonimización depende del tipo de suscripción y del evento que la desencadene. Vea la tabla siguiente para obtener más información.

| Tipo de suscripción                                                                                                                       | Evento que desencadena la anonimización                                                                                                     | Cuando se produce la anonimización |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | El suscriptor deja de participar en el programa o no acepta los términos de uso                                    | 30 días               |
| Suscripciones de Visual Studio compradas a través de Microsoft Store (venta directa)                                                                      | La suscripción caduca o no se activa                                                                   | 360 días                  |
| Suscripciones de Visual Studio adquiridas a través de licencias por volumen, Visual Studio Marketplace (suscripciones de nube) o programas como MPN | La suscripción caduca o no se asigna a un usuario                                                          | 180 días                  |
| Todas las suscripciones                                                                                                                       | Se cierra una cuenta de Azure Active Directory o una cuenta Microsoft (MSA) utilizada para iniciar sesión en la suscripción | Inmediatamente               |
| Todas las suscripciones                                                                                                                       | Se quita un suscriptor del inquilino al que está asociado con la cuenta de Azure Active Directory                                | Inmediatamente               |

## <a name="faq"></a>Preguntas más frecuentes

### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>P:  ¿La anonimización de datos personales del suscriptor causa que pierda el acceso a la suscripción?
R:  No.  La anonimización se produce en respuesta a un evento que provoca la pérdida de acceso a la suscripción, pero no provoca la pérdida de acceso.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>P:  Soy administrador de suscripciones de mi organización.  ¿Si se anonimiza la información de uno de mis suscriptores, esa suscripción puede reasignarse a otro usuario?
R:  Sí, siempre y cuando la suscripción no haya expirado, pueden reasignarse a otro suscriptor.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo evitar la anonimización [vinculando las identidades de AAD y de MSA](/azure/active-directory/b2b/add-users-administrator).

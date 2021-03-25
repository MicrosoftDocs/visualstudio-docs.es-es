---
title: Anonimización de datos de suscriptor de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 03/11/2021
ms.topic: conceptual
description: Obtenga información sobre cómo se anonimizan los datos del suscriptor cuando se pierde el acceso a las suscripciones.
ms.openlocfilehash: 2a3d55824db1c90ff0868dda6d398e8c0e9a53d7
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757612"
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

### <a name="q--im-an-admin-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>P:  Soy administrador de las suscripciones de mi organización.  ¿Si se anonimiza la información de uno de mis suscriptores, esa suscripción puede reasignarse a otro usuario?
R:  Sí.  Se pueden reasignar las suscripciones si se cumplen estos criterios:
- La suscripción no ha expirado.
- Ha transcurrido un mínimo de 90 días desde la última vez que se asignó la suscripción a un suscriptor.  Por ejemplo, si se asignó una suscripción a un suscriptor el 1 de junio, no se podrá reasignar hasta el 30 de agosto.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>P: ¿Cómo se puede evitar la anonimización que provoca la eliminación de una dirección de correo electrónico de inicio de sesión?
R:  Hay dos maneras de impedir la incidencia:
- Implemente un sistema de administración de identidad único, ya sea MSA o AAD, pero no ambos.  
- Asocie las identidades de AAD y MSA a través de los inquilinos. 

## <a name="support-resources"></a>Recursos de soporte técnico
- Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación de Suscripciones de Visual Studio, consulte la página de [soporte técnico para las suscripciones](https://aka.ms/vssubscriberhelp) de Visual Studio.

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga información sobre cómo evitar la anonimización [asociando las identidades de AAD y MSA](/azure/active-directory/b2b/add-users-administrator).
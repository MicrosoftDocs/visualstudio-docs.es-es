---
title: Uso de las identidades conectadas de la cuenta Microsoft y Azure Active Directory | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 09/27/2019
ms.topic: conceptual
robots: noindex, nofollow
description: Aprenda a trabajar con identidades conectadas de la cuenta Microsoft y Azure Active Directory.
ms.openlocfilehash: 1a862caa1f984f5d22f041a6f0cbff6534d8cc1c
ms.sourcegitcommit: bcdab788085bd9931d73883fe70cd5831317dca2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72816581"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Uso de identidades conectadas en suscripciones de Visual Studio
Si recibe una suscripción a Visual Studio por medio de su trabajo o escuela, y usa la cuenta Microsoft (MSA) para iniciar sesión, el administrador de suscripciones puede conectar su MSA a su identidad en la instancia de Azure Active Directory de la organización (Azure AD).  Esto cambiará el modo de acceder a algunas de las ventajas que se incluyen en la suscripción. 

## <a name="overview-of-connected-ids"></a>Introducción a los identificadores conectados
Las organizaciones cambian cada vez más a identidades basadas en Azure AD para proporcionar una mejor seguridad y compatibilidad con la administración automatizada de suscripciones.  Si la suscripción usa una MSA, como @outlook.com u otra dirección de correo electrónico personal, el administrador puede cambiar el correo electrónico de inicio de sesión por su identidad de Azure AD.  Esto cambiará el modo de iniciar sesión en el portal de suscriptores en https://my.visualstudio.com, pero es posible que no cambie el modo de acceder a todas las ventajas.  

Si el administrador conecta sus identidades de MSA y Azure AD, recibirá un correo electrónico para informarle de que el acceso a su suscripción de Visual Studio comenzará con su identidad de Azure AD en lugar de con su MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Acceso a las ventajas mediante las identidades de Azure AD
Después de que el administrador haya conectado su MSA a su identidad de Azure AD, deberá iniciar sesión en el portal de suscriptores en https://my.visualstudio.com con su identidad de Azure AD para acceder a las ventajas basadas en Azure AD.  Se incluyen los siguientes:
- IDE de Visual Studio
- Azure DevOps
- Crédito individual de Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Acceso a las ventajas con la MSA
Muchas ventajas que se ofrecen en las suscripciones de Visual Studio, como Pluralsight, LinkedIn, CloudPilot y demás precisan de la creación de cuentas de usuario en los sitios web de los asociados.  En esas cuentas, debe seguir usando la identidad que usó al crear la cuenta.  Por ejemplo, si activó su ventaja de Pluralsight con su MSA, debe seguir usando su MSA al realizar cursos de Pluralsight, independientemente de la identidad que use para iniciar sesión en el portal de suscriptores.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Uso de una identidad alternativa para acceder a la suscripción
La adición de una cuenta alternativa a la suscripción de Visual Studio permite acceder a las ventajas de la suscripción, como Azure DevOps y Azure, con una identidad diferente a la que se asigna la suscripción. En el pasado, esta funcionalidad solo estaba disponible si la suscripción de Visual Studio (VS) se había asignado a una cuenta Microsoft (MSA). Se ha ampliado esta funcionalidad para cuentas profesionales o educativas de Azure Active Directory (Azure AD).  Para más información sobre el uso de cuentas alternativas, consulte nuestro artículo [Identidades alternativas](vs-alternate-identity.md). 

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q-how-can-i-contact-my-admin-about-this"></a>P: ¿Cómo puedo ponerme en contacto con el administrador sobre esta asunto?
R:  Para información sobre cómo ponerse en contacto con el administrador, consulte el artículo [Cómo ponerse en contacto con el administrador de suscripciones](contact-my-admin.md).  

## <a name="next-steps"></a>Pasos siguientes
Una vez que el administrador conecta sus cuentas de Azure AD y MSA, se recomienda comprobar que puede iniciar sesión correctamente en el [portal de suscripciones](https://my.visualstudio.com?wt.mc_id=o~msft~docs) y acceder a ventajas como Azure DevOps, Visual Studio y el crédito individual de Azure DevTest. 
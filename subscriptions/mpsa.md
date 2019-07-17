---
title: Suscripciones de Visual Studio en un Contrato de servicios y productos de Microsoft (MPSA) | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: conceptual
description: Suscripciones de Visual Studio en un Contrato de servicios y productos de Microsoft (MPSA)
ms.openlocfilehash: 30437703029128232c82d0f4cc4441f09cbd9123
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784401"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Suscripciones de Visual Studio en un Contrato de servicios y productos de Microsoft (MPSA)

Si ha comprado suscripciones de Visual Studio a través del programa MPSA, debe tener en cuenta algunos aspectos antes de poder convertirse en un administrador de suscripciones de Visual Studio y asignar las suscripciones a los usuarios. Si ya lo han configurado como administrador, puede ir directamente al [Portal de administración](https://manage.visualstudio.com/) de suscripciones de Visual Studio.

Como cliente de MPSA, tendrá acceso a un portal en que puede administrar los activos comprados a través de MPSA. Este portal nuevo se denomina [Centro de negocios](https://businessaccount.microsoft.com/), que es compatible con algunas de las funcionalidades antiguas y nuevas como el Centro de servicio de licencias por volumen (VLSC). Estas incluyen ver el resumen de licencias, los pedidos, las descargas, las claves, los usuarios, etcétera. Sin embargo, las suscripciones de Visual Studio en MPSA tienen un comportamiento muy parecido al de Cloud Services. El Centro de negocios también utiliza las cuentas profesionales para iniciar sesión, en lugar de las cuentas de Microsoft. Si en su organización se usan servicios en la nube, como Office 365 o Azure Active Directory, y el correo electrónico forma parte de cualquiera de estos dos servicios, la cuenta ya es una cuenta profesional. Esto le permitirá registrarse en el Centro de negocios con la contraseña existente que su organización le ha asignado. Si en su organización no se usan los servicios en la nube y el correo electrónico no es una cuenta profesional, no se preocupe ya que puede utilizarla para registrarse en el Centro de negocios.

Además, el [Portal de administración](https://manage.visualstudio.com/) de suscripciones de Visual Studio es el lugar en que las suscripciones se asignarán a los suscriptores cuando se convierta en administrador de Visual Studio. En MPSA, las suscripciones de Visual Studio deben proveerse al portal de administración correspondiente, que es el Portal de administración de suscripciones de Visual Studio. Para ello, debe asociar la cuenta de compra a un inquilino (por ejemplo, contoso.onmicrosoft.com).

Tenga en cuenta que hay dos tipos de inquilinos (un inquilino administrado y un inquilino sin administrar). Un inquilino administrado se refiere a un inquilino que la organización ya lo está administrando como administrador.

Un inquilino sin administrar es un inquilino que no cuenta con ningún administrador ni se puede utilizar para los servicios en línea, como Office 365. Los inquilinos sin administrar también se crean al registrarse en el Centro de negocios con un correo electrónico que no es una cuenta profesional. Si le solicitaran que cree una contraseña al registrarse en el Centro de negocios, esto significa que el correo electrónico no era una cuenta profesional y que se creó un inquilino sin administrar.

Antes de completar la asociación del inquilino, presentamos unos requisitos y pasos necesarios para convertirse en administrador de suscripciones de Visual Studio.

## <a name="pre-tenant-association-managed-tenant"></a>Asociación previa al inquilino (inquilino administrado)

- Debe ser un usuario registrado en el Centro de negocios.
- Debe ser un administrador de usuario (como mínimo) o el administrador global del inquilino del que forma parte. (Esto se aplica si en su compañía ya se usan servicios en la nube). Cualquiera de los roles es necesario para ser administrador de suscripciones de Visual Studio.
- Debe ser un administrador global del inquilino del que forma parte para poder asociar su cuenta de compras a su inquilino.
- Debe ser un Administrador de cuentas en el Centro de negocios.
- El campo "País o región" de su perfil de usuario (y de cualquier otro usuario) en [Azure](https://portal.azure.com/) debe rellenarse de forma adecuada según su país (es decir, Estados Unidos, Canadá, etcétera). 

> [!NOTE]
> No es necesario que los usuarios que quiera convertir en administradores de suscripciones de Visual Studio sean usuarios del Centro de negocios, ya que solo deben cumplir los criterios de los pasos 2 y 5.

Una vez que se hayan cumplido los criterios de los 5 pasos anteriores, puede seguir los pasos que se indican a continuación para asociar su cuenta de compras a su inquilino.
1. Inicie sesión en el [Centro de negocios](https://businessaccount.microsoft.com/).
2. Haga clic en la pestaña **Cuenta** y elija **Asociar dominios**.
3. Seleccione la **Cuenta de compras** (si tiene más de una).
4. Seleccione el **inquilino** (es decir, contoso.onmicrosoft.com).
5. Haga clic en **Asociar dominio**.

Tras realizar la asociación, todos los usuarios que cumplan los criterios necesarios normalmente constarán como administradores de suscripciones de Visual Studio al cabo de pocos minutos. Sin embargo, en ocasiones este proceso puede tardar hasta 24 horas. Cuando conste como administrador, podrá tener acceso al Portal de administración de suscripciones de Visual Studio. Si el proceso tarda más de 24 horas, póngase en contacto con el Equipo de Soporte Técnico de MPSA.

> [!NOTE]
> Si hay usuarios nuevos que hayan cumplido los criterios de los pasos 2 y 5 (después de la asociación), debe ponerse en contacto con el Equipo de Soporte Técnico de MPSA. El Equipo de Soporte Técnico de MPSA proporcionará asistencia para proveer los nuevos administradores de suscripciones de Visual Studio.

## <a name="tenant-association-unmanaged"></a>Asociación de inquilino (sin administrar)

Si se ha registrado en el Centro de negocios con un correo electrónico que no era una cuenta profesional (no registrada en Azure Active Directory "Azure AD"), como se explica en el párrafo cinco anterior, la asociación de inquilino será ligeramente diferente. Deberá realizar lo que se conoce como "aceptación de dominio". Durante este proceso, se hará a sí mismo el administrador global, con lo que el inquilino pasará de ser sin administrar a administrado.

Para obtener una explicación más detallada de este proceso, puede consultar las [Guías de inicio rápido](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Descargue la guía denominada *"Instalación y uso de los servicios en línea"* , en que se detalla el proceso de aceptación de dominio. Una vez que haya finalizado este procedimiento, la cuenta de compras también se asociará a su inquilino.

> [!NOTE]
> Una vez completado el proceso de aceptación de dominio, debe atenerse a los criterios de los cinco pasos indicados en la sección Asociación previa al inquilino (administrado). Una vez que se cumplen los criterios, solo será necesario ponerse en contacto con el Equipo de Soporte Técnico de MPSA para proveer más administradores de suscripciones de Visual Studio.

Puede ponerse en contacto con el Equipo de Soporte Técnico por teléfono o correo electrónico si necesita ayuda o tiene alguna pregunta.

Soporte técnico de MPSA: **1-866-200-9611**, disponible de lunes a viernes de 5:30 a 17:30, hora del Pacífico

En línea: https://support.microsoft.com/supportrequestform/2afa6f15-b710-db46-909a-8346017c802f?sl=enampsc=US

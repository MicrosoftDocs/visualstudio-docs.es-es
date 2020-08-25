---
title: Suscripciones de Visual Studio en un Contrato de servicios y productos de Microsoft (MPSA) | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/03/2020
ms.topic: conceptual
description: Suscripciones de Visual Studio en un Contrato de servicios y productos de Microsoft (MPSA)
ms.openlocfilehash: 6ce2208e6d1028e1e697b216d41cdd825dfc0d33
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247316"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Suscripciones de Visual Studio en un Contrato de servicios y productos de Microsoft (MPSA)
Si ha comprado suscripciones de Visual Studio a través del programa MPSA, debe tener en cuenta algunos aspectos antes de poder convertirse en un administrador de suscripciones de Visual Studio y asignar las suscripciones a los usuarios. Si ya lo han configurado como administrador, puede ir directamente al [Portal de administración de suscripciones de Visual Studio](https://manage.visualstudio.com/).

Los clientes de MPSA ahora administran los recursos comprados a través de MPSA en un nuevo portal denominado [Business Center](https://businessaccount.microsoft.com/Customer), que admite funcionalidades similares a las de Microsoft Business Center. Estas incluyen ver el resumen de licencias, los pedidos, las descargas, las claves, los usuarios, etcétera. Sin embargo, las suscripciones de Visual Studio en MPSA tienen un comportamiento muy parecido al de Cloud Services. Business Center también usa las cuentas profesionales para iniciar sesión, en lugar de las cuentas Microsoft (MSA). Si en su organización se usan servicios en la nube, como Office 365 o Azure Active Directory, y el correo electrónico forma parte de cualquiera de estos dos servicios, la cuenta ya es una cuenta profesional. Esta cuenta le permite registrarse en Business Center con la contraseña existente. Si en su organización no se usan los servicios en la nube y el correo electrónico no es una cuenta profesional, que puede usarla para registrarse en Business Center.

Además, el [Portal de administración de suscripciones de Visual Studio](https://manage.visualstudio.com/) es el lugar donde se asignarán las suscripciones a los suscriptores cuando se convierta en administrador de Visual Studio. En MPSA, las suscripciones de Visual Studio deben proporcionarse al portal de administración correspondiente, que es el Portal de administración de suscripciones de Visual Studio. Para ello, debe asociar la cuenta de compra a un inquilino (por ejemplo, contoso.onmicrosoft.com).

Tenga en cuenta que hay dos tipos de inquilinos: administrados y sin administrar. Un inquilino administrado se refiere a un inquilino que ya están administrando los administradores de la organización.

Un inquilino sin administrar es un inquilino que no tiene ningún administrador asignado y no se puede usar para servicios en línea, como Office 365. Los inquilinos sin administrar también se crean al registrarse en Business Center con un correo electrónico que no es una cuenta profesional. Si le solicitan que cree una contraseña al registrarse en Business Center, significa que el correo electrónico no era una cuenta profesional y que se creó un inquilino sin administrar.

Antes de completar la asociación del inquilino, presentamos unos requisitos y pasos necesarios para convertirse en administrador de suscripciones de Visual Studio.

## <a name="pre-tenant-association-managed-tenant"></a>Asociación previa al inquilino (inquilino administrado)
- Debe ser un usuario registrado en el Centro de negocios.
- Debe ser un administrador de usuario (como mínimo) o el administrador global del inquilino del que forma parte. (Esto se aplica si en su compañía ya se usan servicios en la nube). Cualquiera de los roles es necesario para ser administrador de suscripciones de Visual Studio.
- Debe ser un administrador global del inquilino del que forma parte para poder asociar su cuenta de compras a su inquilino.
- Debe ser un Administrador de cuentas en el Centro de negocios.
- El campo "País o región" de su perfil de usuario (y de cualquier otro usuario) en [Azure](https://portal.azure.com/) debe rellenarse de forma adecuada según su país (es decir, Estados Unidos, Canadá, etcétera). 

> [!NOTE]
> No es necesario que los usuarios que quiera convertir en administradores de suscripciones de Visual Studio sean usuarios de Business Center, ya que solo deben cumplir los criterios 2 y 5.

Una vez que se hayan cumplido los criterios anteriores, puede seguir los pasos que se indican a continuación para asociar su cuenta de compras a su inquilino.
1. Inicie sesión en el [Centro de negocios](https://businessaccount.microsoft.com/Customer).
2. Seleccione la pestaña **Cuenta** y elija **Asociar dominios**.
3. Seleccione la **Cuenta de compras** (si tiene más de una).
4. Seleccione el **inquilino** (es decir, contoso.onmicrosoft.com).
5. Seleccione **Asociar dominio**.

Tras realizar la asociación, todos los usuarios que cumplan los criterios necesarios normalmente constarán como administradores de suscripciones de Visual Studio al cabo de pocos minutos. Sin embargo, en ocasiones este proceso puede tardar hasta 24 horas. Cuando finalice, podrá tener acceso al Portal de administración de suscripciones de Visual Studio. Si el proceso tarda más de 24 horas, siga estos pasos para ponerse en contacto con el Equipo de Soporte Técnico de MPSA:
1. Conéctese a <https://www.microsoft.com/licensing/mpsa/default>.
2. Seleccione el menú **Más** en la parte superior de la página. 
3. Seleccione **Soporte técnico**.
4. Seleccione **Soporte técnico de licencias**.
5. Seleccione la opción de soporte técnico que mejor se adapte a sus necesidades. 

> [!NOTE]
> Si hay usuarios nuevos que cumplan los criterios de los pasos 2 y 5 (después de la asociación), debe ponerse en contacto con el servicio de soporte técnico de MPSA. El Equipo de Soporte Técnico de MPSA proporcionará asistencia para proveer los nuevos administradores de suscripciones de Visual Studio.

## <a name="tenant-association-unmanaged"></a>Asociación de inquilino (sin administrar)
Si se ha registrado en Business Centers con un correo electrónico que no es una cuenta profesional (no registrada en Azure Active Directory "Azure AD"), como se explica anteriormente, la asociación del inquilino será ligeramente diferente. Deberá realizar lo que se conoce como "aceptación de dominio". Durante este proceso, se hará a sí mismo el administrador global, con lo que el inquilino pasará de ser sin administrar a administrado.

Para obtener una explicación más detallada de este proceso, puede consultar las [Guías de inicio rápido](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Descargue la guía denominada *"Instalación y uso de los servicios en línea"* , en que se detalla el proceso de aceptación de dominio. Una vez que haya finalizado este procedimiento, la cuenta de compras también se asociará a su inquilino.

> [!NOTE]
> Una vez completado el proceso de aceptación de dominio, debe atenerse a los criterios de los cinco pasos indicados en la sección Asociación previa al inquilino (administrado). Una vez que se cumplen los criterios, solo será necesario ponerse en contacto con el Equipo de Soporte Técnico de MPSA para proveer más administradores de suscripciones de Visual Studio.

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Eliminar suscripciones](delete-license.md)
- [Determinación del uso máximo](maximum-usage.md)

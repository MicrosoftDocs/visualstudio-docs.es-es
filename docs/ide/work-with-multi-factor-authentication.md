---
title: Trabajar con cuentas que requieran la autenticación multifactor
ms.date: 05/27/2020
ms.topic: conceptual
description: Aprenda a usar Visual Studio con cuentas que requieran la autenticación multifactor
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 696664aa5aa92a3e9a675df4803a3e65e3e81f36
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185702"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Cómo usar Visual Studio con cuentas que requieran la autenticación multifactor

Al colaborar con los usuarios externos invitados, es una buena idea proteger sus aplicaciones y datos con directivas de **acceso condicional (CA)** como, por ejemplo, **autenticación multifactor (MFA)** .  

Una vez habilitadas, los usuarios invitados necesitarán algo más que un nombre de usuario y una contraseña para acceder a los recursos y tendrán que cumplir requisitos de seguridad adicionales. Las directivas de MFA se pueden exigir en el nivel de inquilino, aplicación o usuario invitado individual, del mismo modo que pueden habilitarse para miembros de la organización. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>¿Cómo afectan las directivas de MFA a la experiencia de Visual Studio?
Es posible que las versiones de Visual Studio anteriores a 16.6 tengan experiencias de autenticación degradadas cuando se usan con cuentas que han habilitado directivas de CA como MFA y están asociadas a dos o más inquilinos.

Estos problemas pueden hacer que la instancia de Visual Studio solicite la reautenticación varias veces al día. Tal vez tenga que volver a escribir sus credenciales para inquilinos anteriormente autenticados, incluso durante el transcurso de una misma sesión de Visual Studio.

## <a name="using-visual-studio-with-mfa-policies"></a>Uso de Visual Studio con directivas de MFA
En la versión 16.6, se han agregado nuevas funcionalidades a Visual Studio 2019 que agilizan la forma en que los usuarios pueden acceder a los recursos protegidos mediante directivas de CA como MFA. Para usar este flujo de trabajo mejorado, deberá optar por usar el explorador web predeterminado del sistema como mecanismo para agregar y volver a autenticar las cuentas de Visual Studio.  

> [!WARNING]
> No usar este flujo de trabajo podría desencadenar una experiencia degradada que se tradujese en múltiples peticiones de autenticación adicionales al agregar o volver a autenticar cuentas de Visual Studio. 

### <a name="enabling-system-web-browser"></a>Habilitación del explorador web del sistema  
Para habilitar este flujo de trabajo, vaya al cuadro de diálogo Opciones de Visual Studio **(Herramientas > Opciones...)** , seleccione la pestaña **Cuentas** y elija **Explorador web del sistema** en la lista desplegable **Agregar y volver a autenticar cuentas con:** 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Selección del explorador web del sistema en el menú.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Inicio de sesión en cuentas adicionales con directivas de MFA 
Una vez habilitado el flujo de trabajo del explorador web del sistema, puede iniciar sesión o agregar cuentas a Visual Studio como lo haría normalmente, a través del cuadro de diálogo Configuración de la cuenta **(Archivo > Configuración de la cuenta…)** .   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Adición de una nueva cuenta de personalización a Visual Studio." border="false":::

Esta acción abrirá el explorador web predeterminado del sistema, le pedirá que inicie sesión en su cuenta y valide cualquier directiva de MFA necesaria. 

> [!NOTE] 
> Mantenga el explorador abierto en todo el proceso para obtener la mejor experiencia, ya que al cerrarlo se podrían desencadenar mensajes de autorización adicionales. 

## <a name="reauthenticating-an-account"></a>Reautenticación de una cuenta  
Si hay algún problema con su cuenta, es posible que Visual Studio le pida que vuelva a escribir sus credenciales de cuenta.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Reautenticación de la cuenta de Visual Studio.":::

Al hacer clic en **Vuelva a escribir las credenciales** se abrirá el explorador web predeterminado del sistema e intentará actualizar las credenciales automáticamente. Si no se realiza correctamente, se le pedirá que inicie sesión en su cuenta y valide cualquier directiva de MFA necesaria. 

> [!NOTE] 
> Mantenga el explorador abierto a través de todo el proceso para obtener la mejor experiencia, ya que el cierre del explorador puede desencadenar mensajes de autorización adicionales. 

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Cómo desactivar el uso de un inquilino de Azure Active Directory concreto en Visual Studio

Visual Studio 2019 versión 16.6 ofrece la flexibilidad de filtrar inquilinos específicos, lo que los oculta en Visual Studio. El filtrado elimina la necesidad de autenticarse con ese inquilino, pero también significa que no se podrá acceder a los recursos asociados. 

Esta funcionalidad resulta útil cuando se tienen varios inquilinos, pero se quiere optimizar el entorno de desarrollo teniendo como destino un subconjunto específico. También puede ayudar en aquellos casos en los que no se puede validar una directiva de entidad de certificación o MFA determinada, ya que se puede filtrar el inquilino en conflicto. 

### <a name="how-to-filter-out-a-tenant"></a>Cómo filtrar un inquilino
Para filtrar inquilinos asociados a su cuenta de Visual Studio, abra el cuadro de diálogo Configuración de la cuenta **(Archivo > Configuración de la cuenta...)** y haga clic en **Aplicar filtro**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Selección de Aplicar filtro." border="false":::

Aparecerá el cuadro de diálogo **Filtro de cuenta**, que le permite seleccionar qué inquilinos desea usar con su cuenta. 

:::image type="content" source="media/select-filter-account.png" alt-text="Selección de la cuenta que se va filtrar.":::

## <a name="see-also"></a>Vea también

- [Inicio de sesión en Visual Studio](signing-in-to-visual-studio.md)
- [Iniciar sesión en Visual Studio para Mac](/visualstudio/mac/signing-in)
- [Trabajar con varias cuentas de usuario](work-with-multiple-user-accounts.md)
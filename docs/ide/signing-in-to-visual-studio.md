---
title: Iniciar sesión en Visual Studio
description: Aprenda a iniciar sesión en Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 749814dc6fd20107a2a1d2d5c0c26c7a4bad421b
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296812"
---
# <a name="sign-in-to-visual-studio"></a>Iniciar sesión en Visual Studio

Puede personalizar y optimizar la experiencia de desarrollo en Visual Studio iniciando sesión en la cuenta de personalización.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Iniciar sesión en Visual Studio para Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! ADVERTENCIA] El uso de Visual Studio 2017 para acceder a los recursos configurados para el acceso condicional puede desencadenar una experiencia de autenticación degradada, que solicita la reautenticación varias veces dentro de la misma sesión de Visual Studio. 
> Para trabajar con los recursos configurados para el acceso condicional, actualice a Visual Studio 2019 Update 16.6 o posterior. Para más información, consulte [Cómo usar Visual Studio con cuentas que requieran la autenticación multifactor](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>¿Por qué debo iniciar sesión en Visual Studio?

Cuando inicia sesión, obtiene una experiencia de Visual Studio más enriquecida. Por ejemplo, después de iniciar sesión, puede [sincronizar la configuración](synchronized-settings-in-visual-studio.md) de todos los dispositivos, extender una versión de evaluación y conectarse automáticamente a un servicio de Azure, etc.

Esta es una lista completa de lo que puede esperar y lo que puede hacer después de iniciar sesión:
- **Extensión del período de prueba de Visual Studio**: puede usar Visual Studio Professional o Visual Studio Enterprise durante 90 días más, en lugar de disponer del período de prueba limitado de 30 días. Para ver más información, consulte [Ampliar una versión de prueba o actualizar una licencia](../ide/how-to-unlock-visual-studio.md).

- **Continuación del uso de Visual Studio Community**: si la instalación de la edición Community solicita una licencia, inicie sesión en el IDE para seguir usando Visual Studio Community **gratis**. 

- **Desbloqueo de Visual Studio si usa una cuenta asociada con una suscripción de Visual Studio o una organización de Azure DevOps**. Para ver instrucciones detalladas, consulte [Ampliar una versión de prueba o actualizar una licencia](../ide/how-to-unlock-visual-studio.md).

- **Acceso al programa Visual Studio Dev Essentials**: este programa incluye ofertas de software gratis, aprendizaje, soporte técnico y mucho más. Consulte [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) para obtener más información

- **Sincronización de la configuración de Visual Studio**: la configuración que ha personalizado, como los enlaces de teclado, el diseño de ventana y el tema de color, se aplica inmediatamente al iniciar sesión en Visual Studio en cualquier dispositivo. Vea [Sincronizar la configuración de Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Conexión automática a distintos servicios, por ejemplo, Azure y Azure DevOps Services**, en el IDE sin que se vuelvan a solicitar las credenciales de la misma cuenta.

## <a name="how-to-sign-in-to-visual-studio"></a>Cómo iniciar sesión en Visual Studio

La primera vez que abre Visual Studio, se le pide que inicie sesión y que proporcione información de registro básica.

![Solicitud de inicio de sesión](../ide/media/vs2019_signinpopup.png)

Debe elegir una cuenta Microsoft o una cuenta profesional o educativa que mejor le represente. Si no dispone de ninguna, puede crear una cuenta Microsoft de forma gratuita haciendo clic en el vínculo que aparece debajo del botón de inicio de sesión. Si no lo consigue, vea [¿Cómo suscribirse para obtener una cuenta Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

A continuación, elija la configuración de UI y el tema de color que desea usar en Visual Studio. Visual Studio recordará la configuración y la sincronizará en todos los entornos de Visual Studio en los que ha iniciado sesión. Para obtener una lista de las configuraciones sincronizadas, vea [Configuración sincronizada](../ide/synchronized-settings-in-visual-studio.md). Puede cambiar la configuración más adelante si abre el menú **Herramientas** > **Opciones** en Visual Studio.

Después de proporcionar la configuración, se inicia Visual Studio, y ya ha iniciado sesión y está listo para empezar. Para comprobar si ha iniciado sesión, busque su nombre en la esquina superior derecha del entorno de Visual Studio.

![Usuario actualmente registrado en VS2019](../ide/media/vs2019_username.png)

Si decide no iniciar sesión cuando abra Visual Studio por primera vez, es fácil hacerlo más adelante. Busque el vínculo **Iniciar sesión** situado en la esquina superior derecha del entorno de Visual Studio.

![Usuario que no ha iniciado sesión](../ide/media/vs2019_usernotsignedin.png)

A menos que cierre sesión, siempre que inicia Visual Studio se inicia sesión automáticamente y todos los cambios realizados en la configuración sincronizada se aplican automáticamente. Para cerrar sesión, haga clic en el icono con el nombre del perfil en la esquina superior derecha del entorno de Visual Studio, elija el comando **Configuración de la cuenta** y, después, elija el vínculo **Cerrar sesión**. Para volver a iniciar sesión, elija el comando **Iniciar sesión** situado en la esquina superior derecha del entorno de Visual Studio.

## <a name="to-change-your-profile-information"></a>Para cambiar la información del perfil

1. Vaya a **Archivo** > **Configuración de la cuenta** y elija el vínculo **Administrar perfil de Visual Studio**.

1. En la ventana del explorador, seleccione **Editar perfil** y cambie los valores de configuración que quiera.

1. Cuando haya terminado, presione **Guardar cambios**.

## <a name="troubleshooting"></a>Solución de problemas

Si encuentra algún problema al iniciar sesión, vea la página de [soporte técnico de suscripciones](https://visualstudio.microsoft.com/subscriptions/support/) para obtener ayuda.

## <a name="see-also"></a>Vea también

* [Ampliación de una versión de prueba o actualización de una licencia](../ide/how-to-unlock-visual-studio.md)
* [Trabajar con cuentas de GitHub en Visual Studio](../ide/work-with-github-accounts.md)
* [Introducción al IDE de Visual Studio](../get-started/visual-studio-ide.md)
* [Iniciar sesión (Visual Studio para Mac)](/visualstudio/mac/signing-in)
* [Activación (Visual Studio para Mac)](/visualstudio/mac/activation)

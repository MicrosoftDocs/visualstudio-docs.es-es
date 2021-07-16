---
title: Inicio de sesión
description: Inicio de sesión en Visual Studio para ampliar el periodo de prueba, desbloquear Visual Studio y mucho más
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b4c91a2ff4693b62ce8ac4d40d493995c52b81b
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549477"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Inicio de sesión en Visual Studio en Windows 

Aunque no tiene que iniciar sesión, hacerlo ofrece muchas ventajas. En este artículo, obtendrá información sobre cómo [iniciar sesión](#how-to-sign-in), [actualizar el perfil](#update-your-profile) y las ventajas de la experiencia de Visual Studio. 

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Iniciar sesión en Visual Studio para Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Para trabajar con los recursos configurados para el acceso condicional, actualice a Visual Studio 2019 Update 16.6 o posterior. Para más información, consulte [Cómo usar Visual Studio con cuentas que requieran la autenticación multifactor](work-with-multi-factor-authentication.md).
> El uso de Visual Studio 2017 a fin de acceder a los recursos configurados para el acceso condicional puede desencadenar una experiencia de autenticación degradada, que solicita la reautenticación varias veces dentro de la misma sesión de Visual Studio. 
> 
::: moniker-end

Esta es una lista completa de lo que puede esperar y lo que puede hacer después de iniciar sesión:

|Prestación|Descripción|
|---|---|
|Ampliación del período de prueba de Visual Studio|Use Visual Studio Professional o Visual Studio Enterprise **durante 90 días más**, en lugar de disponer del período de prueba limitado de 30 días. <br/>Vea [Ampliación de una versión de prueba o actualización de una licencia](../ide/how-to-unlock-visual-studio.md).|
|Desbloqueo de Visual Studio (suscripción de Visual Studio o una organización de Azure DevOps)|Desbloqueo de Visual Studio si usa una cuenta asociada con una suscripción de Visual Studio o una organización de Azure DevOps.<br/>Vea [Ampliación de una versión de prueba o actualización de una licencia](../ide/how-to-unlock-visual-studio.md).|
|Sincronización de la configuración de Visual Studio|La configuración que personalice, como los enlaces de teclado, el diseño de ventana y el tema de color, se aplica inmediatamente al iniciar sesión en Visual Studio en cualquier dispositivo. <br/>Vea [Sincronizar la configuración de Visual Studio](../ide/synchronized-settings-in-visual-studio.md).|
|Conexión automática a los servicios|Conéctese a servicios, como Azure y Azure DevOps Services, en el IDE sin que se vuelvan a solicitar las credenciales de la misma cuenta.|
|Seguir usando la edición Visual Studio Community|Si la instalación de la edición Community solicita una licencia, inicie sesión en el IDE para seguir usando Visual Studio Community de **gratuita**. |
|Obtención de "Visual Studio Dev Essentials"|Este programa incluye ofertas de software gratuitas, entrenamiento, soporte técnico y mucho más. <br/>Vea [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/).|


## <a name="how-to-sign-in"></a>Inicio de sesión 

La primera vez que abre Visual Studio, se le pide que inicie sesión y que proporcione información de registro básica.

![Solicitud de inicio de sesión](../ide/media/vs2019_signinpopup.png)

1. Elija una cuenta Microsoft o una cuenta profesional o educativa que mejor le represente. Si no dispone de ninguna, puede crear una cuenta Microsoft de forma gratuita haciendo clic en el vínculo que aparece debajo del botón de inicio de sesión. Si no lo consigue, vea [¿Cómo suscribirse para obtener una cuenta Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Elija la configuración de la interfaz de usuario y el tema de color que quiera usar en Visual Studio. Visual Studio recordará la configuración y la sincronizará en todos los entornos de Visual Studio en los que ha iniciado sesión. Para obtener una lista de las configuraciones sincronizadas, vea [Configuración sincronizada](../ide/synchronized-settings-in-visual-studio.md). Puede cambiar la configuración más adelante si abre el menú **Herramientas** > **Opciones** en Visual Studio.
   Después de proporcionar la configuración, se inicia Visual Studio, y ya ha iniciado sesión y está listo para empezar. 
   
1. Para comprobar si ha iniciado sesión, busque su nombre en la esquina superior derecha del entorno de Visual Studio.

![Usuario actualmente registrado en VS2019](../ide/media/vs2019_username.png)

Si decide no iniciar sesión cuando abra Visual Studio por primera vez, es fácil hacerlo más adelante. Busque el vínculo **Iniciar sesión** situado en la esquina superior derecha del entorno de Visual Studio.

![Usuario que no ha iniciado sesión](../ide/media/vs2019_usernotsignedin.png)

A menos que cierre sesión, siempre que inicia Visual Studio se inicia sesión automáticamente y todos los cambios realizados en la configuración sincronizada se aplican automáticamente. Para cerrar sesión, haga clic en el icono con el nombre del perfil en la esquina superior derecha del entorno de Visual Studio, elija el comando **Configuración de la cuenta** y, después, elija el vínculo **Cerrar sesión**. Para volver a iniciar sesión, elija el comando **Iniciar sesión** situado en la esquina superior derecha del entorno de Visual Studio.

## <a name="update-your-profile"></a>Actualización del perfil

1. Vaya a **Archivo** > **Configuración de la cuenta** y elija el vínculo **Administrar perfil de Visual Studio**.

1. En la ventana del explorador, seleccione **Editar perfil** y cambie los valores de configuración que quiera.

1. Cuando haya terminado, presione **Guardar cambios**.

## <a name="troubleshooting"></a>Solución de problemas

Vea la página [Soporte técnico de la suscripción](https://visualstudio.microsoft.com/subscriptions/support/) para obtener ayuda.

---
title: Trabajar con cuentas de GitHub en Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Aprenda a usar Visual Studio con cuentas de GitHub.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 845b663a3a0828806766fa0609e45efafabec50a
ms.sourcegitcommit: e8a13978131f257d91ce37c5a2e0d153a4c400ef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704032"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Trabajar con cuentas de GitHub en Visual Studio

Si tiene una cuenta pública de GitHub o GitHub Enterprise, puede agregarla a su cadena de claves de Visual Studio. Después de agregar la cuenta, podrá aprovechar la integración de la plataforma, ya que podrá crear repositorios de GitHub y acceder a ellos directamente desde Visual Studio.

## <a name="adding-public-github-accounts"></a>Adición de cuentas públicas de GitHub

Si ya ha iniciado sesión en Visual Studio con una cuenta de Microsoft, o una cuenta profesional o educativa, puede agregar la cuenta de GitHub pública.

1. Seleccione el icono con sus iniciales en la esquina superior derecha del entorno de Visual Studio. Luego, seleccione **Configuración de la cuenta...** para administrar las cuentas. También puede abrir el cuadro de diálogo Configuración de la cuenta desde **Archivo** > **Configuración de la cuenta**.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Configuración de la cuenta":::

2. En el submenú **Todas las cuentas**, seleccione el signo más para agregar una cuenta y elija **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Selección de Agregar cuenta de GitHub.":::

3. Se le redirigirá al explorador, donde puede iniciar sesión con sus credenciales de GitHub. Después de iniciar sesión, se mostrará una ventana en el explorador para indicar que la operación se ha realizado correctamente; ahora, puede volver a Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Ventana de operación correcta en el explorador":::

4. Ambas cuentas estarán en el submenú **Todas las cuentas**.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Ambas cuentas mostradas":::

Si aún no ha iniciado sesión en Visual Studio con una cuenta diferente, seleccione el vínculo **Iniciar sesión** en la esquina superior derecha del entorno de Visual Studio. También puede abrir el cuadro de diálogo Configuración de la cuenta desde **Archivo** > **Configuración de la cuenta**. A continuación, siga las instrucciones anteriores para agregar su cuenta de GitHub.

![Usuario que no ha iniciado sesión](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Adición de cuentas de GitHub Enterprise

De forma predeterminada, Visual Studio solo tiene habilitadas cuentas públicas de GitHub.

1. Para habilitar cuentas empresariales de GitHub, vaya a **Herramientas** > **Opciones** y busque las opciones **Cuentas**.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menú de opciones de cuentas":::

2. A continuación, active la casilla **Include GitHub Enterprise Server accounts** (Incluir cuentas de servidor de GitHub Enterprise). La próxima vez que vaya a **Configuración de la cuenta** e intente agregar una cuenta de GitHub, verá opciones para GitHub y GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Inicio de sesión con GitHub Enterprise":::

3. Después de escribir la dirección del servidor de GitHub Enterprise, seleccione **Sign in with your browser** (Iniciar sesión con el explorador). Allí, puede iniciar sesión con sus credenciales de GitHub Enterprise.

## <a name="see-also"></a>Consulte también

- [Trabajar con varias cuentas de usuario](work-with-multiple-user-accounts.md)
- [Inicio de sesión en Visual Studio](signing-in-to-visual-studio.md)

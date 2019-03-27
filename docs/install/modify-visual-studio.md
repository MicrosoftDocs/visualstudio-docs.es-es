---
title: Modificar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo modificar Visual Studio, paso a paso.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 06/12/2018
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 14b80de86c39f9c6ca253434fa90b9f1a4839df2
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324901"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modificación de Visual Studio mediante la incorporación o la eliminación de cargas de trabajo y componentes

No solo le hemos facilitado la personalización de Visual Studio para que se adapte a las tareas que quiere realizar, sino que también hemos facilitado su personalización. Para ello, inicie el nuevo instalador de Visual Studio y realice los cambios que quiera.

Esta es la manera de hacerlo.

## <a name="modify-workloads"></a>Modificar cargas de trabajo

 Las cargas de trabajo contienen las características que necesita para el lenguaje de programación o la plataforma que está usando. Use cargas de trabajo para modificar Visual Studio de manera que admita el trabajo que quiere realizar, cuando quiera.

>[!IMPORTANT]
>Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).

1. Busque el instalador de Visual Studio en su equipo.

     Por ejemplo, en un equipo que ejecuta Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.

     ![Instalador de Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Encontrar el instalador de Microsoft Visual Studio")

     >[!NOTE]
     >En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).<br/><br/> Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2. Haga clic o pulse para iniciar el instalador y, después, elija **Modificar**.

     ![Inicio o modificación de Visual Studio](media/modify-visual-studio.png "Modificación de Visual Studio 2017")

     Si tiene una actualización pendiente, el botón Modificar se encuentra en otro lugar. De este modo, puede modificar Visual Studio sin actualizar, si decide hacerlo. Haga clic en **Más** y, a continuación, elija **Modificar**.

     ![Actualización o modificación de Visual Studio](media/modify-or-update-visual-studio.png "Actualización o modificación de Visual Studio 2017")

3. Desde la pantalla **Cargas de trabajo**, seleccione o anule la selección de las cargas de trabajo que quiere instalar o desinstalar.

    ![Cuadro de diálogo de instalación de Visual Studio 2017](media/vs2017-modify-workloads.PNG "Selección de una carga de trabajo en Visual Studio 2017")

4. Vuelva a elegir **Modificar**.

5. Después de que se instalen los nuevos componentes y cargas de trabajo, elija **Iniciar**.

## <a name="modify-individual-components"></a>Modificar componentes individuales

Si no quiere usar la característica útil de cargas de trabajo para personalizar la instalación de Visual Studio, elija la opción **Componentes individuales** del instalador de Visual Studio, seleccione lo que quiera y, después, siga las indicaciones.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)

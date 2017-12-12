---
title: "Modificación de Visual Studio 2017 | Microsoft Docs"
description: "Obtenga información sobre cómo modificar Visual Studio, paso a paso."
ms.custom: H1Hack27Feb2017
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: d35d3e5b58ad9aed66bd85f445f03b28a931a725
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Modificación de Visual Studio 2017 mediante la incorporación o la eliminación de cargas de trabajo y componentes
No solo le hemos facilitado la personalización de Visual Studio para que se adapte a las tareas que quiere realizar, sino que también hemos facilitado su personalización. Ya no tiene que ir al Panel de control para esto; en su lugar, inicie el nuevo Instalador de Visual Studio y realice los cambios que quiera.

Esta es la manera de hacerlo.  

## <a name="modify-workloads"></a>Modificar cargas de trabajo  
 Las cargas de trabajo contienen las características que necesita para el lenguaje de programación o la plataforma que está usando. Use cargas de trabajo para modificar Visual Studio de manera que admita el trabajo que quiere realizar, cuando quiera.  

>[!IMPORTANT]
>Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).

1.  Busque el instalador de Visual Studio en su equipo.  

     Por ejemplo, en un equipo que ejecuta la Actualización de aniversario de Windows 10, seleccione **Iniciar** y, después, desplácese hasta la letra **I** donde lo verá como **Instalador de Visual Studio**.  

     ![Instalador de Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Encontrar el instalador de Microsoft Visual Studio")

     >[!NOTE]
     En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).<br/><br/> Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2.  Haga clic o pulse para iniciar el instalador y, después, seleccione **Modificar**.  

     ![Inicio o modificación de Visual Studio](media/vs2017-modify.PNG "Modificación de Visual Studio 2017")  

3.  Desde la pantalla **Cargas de trabajo**, seleccione o anule la selección de las cargas de trabajo que quiere instalar o desinstalar.  

    ![Cuadro de diálogo de instalación de Visual Studio 2017](media/vs2017-modify-workloads.PNG "Selección de una carga de trabajo en Visual Studio 2017")

4. Haga clic o pulse **Modificar** de nuevo.  

5. Después de que se instalen los nuevos componentes y cargas de trabajo, haga clic en **Iniciar**.

## <a name="modify-individual-components"></a>Modificar componentes individuales

Si no quiere usar la característica útil de cargas de trabajo para personalizar la instalación de Visual Studio, pulse la opción **Componentes individuales** desde el instalador de Visual Studio, seleccione lo que quiera y, después, siga las indicaciones.  

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, vea sugerencias para la solución de problemas en la página [Solucionar problemas de errores de instalación y actualización de Visual Studio 2017](troubleshooting-installation-issues.md). También puede informarnos de problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) del IDE de Visual Studio o compartir una sugerencia con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579). Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), hacer preguntas y encontrar respuestas. También puede comunicarse con nosotros y con otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la Comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio) (requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también
* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
* [Cómo notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

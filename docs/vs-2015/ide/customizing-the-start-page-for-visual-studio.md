---
title: Personalizar la página principal | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c771d45cc4d29fc718f39bb09254afe5fee02249
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940724"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personalizar la página principal de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay varias formas predeterminadas de personalizar la página principal de Visual Studio: se puede mostrar el cuadro de diálogo **Abrir proyecto** o abrir la solución que se ha cargado en último lugar. También puede mostrar una página principal personalizada, que es una página XAML de Windows Presentation Foundation (WPF), que se ejecuta en una ventana de herramientas y ejecuta comandos internos de Visual Studio.

## <a name="customizing-the-default-start-page"></a>Personalizar la página principal predeterminada

1.  En la barra de menús, elija **Herramientas**, **Opciones**.

2.  Expanda **Entorno** y después elija **Inicio**.

3.  En la lista **Al inicio**, elija el elemento que quiera personalizar.

## <a name="show-a-custom-start-page"></a>Mostrar una página principal personalizada

1.  Instale una página principal personalizada de una de las siguientes maneras:

    -   Instálela de la [Galería de Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), de otro sitio web o de una página de su intranet local.

        > [!NOTE]
        >  Si le gusta una página de una versión anterior de Visual Studio, puede actualizarla con Visual Studio SDK. Vea [Cómo: Actualizar una página de inicio personalizada de Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Abra un archivo .vsix que contenga una página principal personalizada, o copie y pegue los archivos de la página principal en la carpeta **%USERPROFILE%\Mis documentos\Visual Studio 2015\StartPages** del equipo.

    -   Cree su propia página principal si ha instalado Visual Studio SDK.

         Consulte [crear su propia página de inicio](../misc/creating-your-own-start-page.md).

2.  En la barra de menús, elija **Herramientas**, **Opciones**.

3.  Expanda **Entorno** y después elija **Inicio**.

4.  En la lista **Personalizar página principal**, seleccione la página que quiera.

> [!NOTE]
>  Si un error de una página principal personalizada hace que Visual Studio se bloquee, inicie Visual Studio en modo seguro y después establezca que se use la página principal predeterminada. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vea también
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [crear su propia página de inicio](../misc/creating-your-own-start-page.md)

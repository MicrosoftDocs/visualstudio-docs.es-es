---
title: "Personalizar la página principal de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Personalizar la página principal de Visual Studio
Hay varias formas predeterminadas de personalizar la página principal de Visual Studio: se puede mostrar el cuadro de diálogo **Abrir proyecto** o abrir la solución que se ha cargado en último lugar. También puede mostrar una página principal personalizada, que es una página XAML de Windows Presentation Foundation (WPF), que se ejecuta en una ventana de herramientas y ejecuta comandos internos de Visual Studio.  

## <a name="customize-the-default-start-page"></a>Personalizar la página principal predeterminada  

1.  En la barra de menús, elija **Herramientas**, **Opciones**.  

2.  Expanda **Entorno** y después elija **Inicio**.  

3.  En la lista **Al inicio**, elija el elemento que quiera personalizar.  

## <a name="show-a-custom-start-page"></a>Mostrar una página principal personalizada  

1.  Instale una página principal personalizada de una de las siguientes maneras:  

    -   Instálela de la [Galería de Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), de otro sitio web o de una página de su intranet local.  

        Abra un archivo .vsix que contenga una página principal personalizada, o copie y pegue los archivos de la página principal en la carpeta **%USERPROFILE%\Mis documentos\Visual Studio 2017\StartPages** del equipo.  

    -   Cree su propia página principal si ha instalado Visual Studio SDK.  

         Consulte [Crear una página principal personalizada](../extensibility/creating-a-custom-start-page.md).  

2.  En la barra de menús, elija **Herramientas**, **Opciones**.  

3.  Expanda **Entorno** y después elija **Inicio**.  

4.  En la lista **Personalizar página principal**, seleccione la página que quiera.  

> [!NOTE]
>  Si un error de una página principal personalizada hace que Visual Studio se bloquee, inicie Visual Studio en modo seguro y después establezca que se use la página principal predeterminada. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>Vea también  
 [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md)   

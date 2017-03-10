---
title: "Personalizar la página principal de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
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
caps.latest.revision: 45
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d797017eb46f38a81f4d5ba6f1999457aa816d1c
ms.openlocfilehash: 69cc33533afd449e50bfc3ecbc8384359253fabb
ms.lasthandoff: 02/22/2017

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
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   


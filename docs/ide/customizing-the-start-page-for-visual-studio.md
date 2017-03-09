---
title: "Personalizar la p&#225;gina principal de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.startpage"
  - "VS.StartPage.HowDoI"
  - "vs.ToolsOptionsPages.Startup"
helpviewer_keywords: 
  - "personalizar la página principal [Visual Studio]"
  - "página principal [Visual Studio]"
  - "página principal de Visual Studio"
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
caps.handback.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Personalizar la p&#225;gina principal de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay varias formas de personalizar de manera predeterminada la página principal de Visual Studio: se puede mostrar el cuadro de diálogo **Abrir proyecto** o abrir la solución que se cargó en último lugar.  También puede mostrar una página principal personalizada, que es una página XAML de Windows Presentation Foundation \(WPF\), que se ejecuta en una ventana de herramientas y ejecuta comandos internos de Visual Studio.  
  
## Personalizar la página principal predeterminada  
  
1.  En la barra de menús, elija **Herramientas**, **Opciones**.  
  
2.  Expanda **Entorno** y elija **Inicio**.  
  
3.  En la lista **Al inicio**, elija el elemento que desee personalizar.  
  
## Mostrar una página principal personalizada  
  
1.  Instale una página principal personalizada de una de las siguientes maneras:  
  
    -   Instálela desde la [Galería de Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), desde otro sitio web o desde una página de la intranet local.  
  
        > [!NOTE]
        >  Si le gusta una página de una versión anterior de Visual Studio, puede actualizarla con Visual Studio SDK.  Consulte este artículo sobre [Cómo: Actualizar una página de inicio personalizada de Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
         Abra un archivo .vsix que contenga una página de inicio personalizada, o copie y pegue los archivos de la página de inicio en la carpeta %USERPROFILE%\\Mis documentos\\Visual Studio 2015\\StartPages del equipo.  
  
    -   Cree su propia página principal si ha instalado Visual Studio SDK.  
  
         Consulte este artículo sobre las [Crear su propia página de inicio](../misc/creating-your-own-start-page.md).  
  
2.  En la barra de menús, elija **Herramientas**, **Opciones**.  
  
3.  Expanda **Entorno** y elija **Inicio**.  
  
4.  En la lista **Personalizar página principal**, seleccione la página que desea.  
  
> [!NOTE]
>  Si un error de una página principal personalizada hace que Visual Studio se bloquee, inicie Visual Studio en modo seguro y después establezca que se use la página principal predeterminada.  Consulte [\/SafeMode](../ide/reference/safemode-devenv-exe.md).  
  
## Vea también  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Crear su propia página de inicio](../misc/creating-your-own-start-page.md)
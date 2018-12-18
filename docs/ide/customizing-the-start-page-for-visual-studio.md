---
title: Instalación de una página de inicio personalizada o cambio del elemento de inicio en Visual Studio
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5e32a311bcd60542df80518c791b1fbe413a7b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916612"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Personalizar la página principal de Visual Studio

Hay varias formas diferentes de personalizar la experiencia de inicio de Visual Studio: se puede mostrar el cuadro de diálogo **Abrir proyecto** o abrir la solución que se ha cargado en último lugar. También puede mostrar una página principal personalizada, que es una página XAML de Windows Presentation Foundation (WPF), que se ejecuta en una ventana de herramientas y ejecuta comandos internos de Visual Studio.

## <a name="to-change-the-startup-item"></a>Para cambiar la pantalla de inicio

1. En la barra de menús, elija **Herramientas** > **Opciones**.

1. Expanda **Entorno** y después elija **Inicio**.

1. En la lista **Al iniciar el sistema**, seleccione el elemento que se mostrará después del inicio de Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Para mostrar una página principal personalizada

Puede [crear su propia página de inicio personalizada](../extensibility/creating-a-custom-start-page.md) mediante el SDK de Visual Studio, o usar una que alguien más ya haya creado. Por ejemplo, puede encontrar páginas de inicio personalizadas en [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Para instalar una página de inicio personalizada, abra el archivo *.vsix* o copie y pegue los archivos de la página principal en la carpeta *%USERPROFILE%\Documentos\Visual Studio 2017\StartPages* del equipo.

### <a name="to-select-which-custom-start-page-to-display"></a>Para seleccionar la página de inicio personalizada que se va a mostrar

1. En la barra de menús, elija **Herramientas** > **Opciones**.

1. Expanda **Entorno** y después elija **Inicio**.

1. En la lista **Personalizar página principal**, seleccione la página que quiera.

> [!NOTE]
> Si un error de una página principal personalizada hace que Visual Studio se bloquee, inicie Visual Studio en modo seguro y después establezca que se use la página principal predeterminada. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vea también

- [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md)
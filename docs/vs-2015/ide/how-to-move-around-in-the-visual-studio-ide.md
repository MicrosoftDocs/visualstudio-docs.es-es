---
title: Procedimiento Moverse por el IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94629a2e64d154313711b3e8968b28959d3341e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805424"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Procedimiento Moverse por el IDE de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El entorno de desarrollo integrado (IDE) se ha diseñado para permitir el movimiento entre ventanas y archivos de varias maneras, dependiendo de los requisitos del proyecto o de sus preferencias. Puede desplazarse por los archivos abiertos en el editor o desplazarse por todas las ventanas de las herramientas activas en el IDE. También puede cambiar directamente a cualquier archivo abierto en el editor, sin tener en cuenta el orden en el que se accedió por última vez. Estas características pueden ayudar a aumentar la productividad al trabajar en el IDE.

> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Esta página de Ayuda se ha redactado teniendo en cuenta la **Configuración general de desarrollo**. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Métodos abreviados de teclado
 Prácticamente cualquier comando de menú en Visual Studio tiene un método abreviado de teclado. También puede crear sus propias combinaciones de teclas personalizadas. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Navegar entre archivos en el Editor
 Puede utilizar varios métodos para desplazarse por los archivos abiertos en el editor. Puede moverse entre los archivos en el orden en el que accedió a ellos: utilice el navegador del IDE para encontrar rápidamente cualquier archivo abierto o para anclar archivos favoritos a la pestaña para que siempre estén visibles.

 Puede navegar hacia atrás y hacia delante por los archivos abiertos en el editor según el orden en el que se accedió a ellos; se parece a las opciones Atrás y Adelante que se utilizan para ver el historial de Microsoft Internet Explorer.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Para desplazarse por los archivos abiertos por orden de uso

- Para activar los documentos abiertos en el orden de acceso más reciente, presione CTRL + signo menos.

- Para activar los documentos abiertos en el orden inverso, presione CTRL + MAYÚS + signo menos.

  > [!NOTE]
  >  **Navegar hacia atrás** y **Navegar hacia delante** también se pueden encontrar en el menú **Ver**.

  También puede cambiar a un archivo concreto abierto en el editor sin tener en cuenta el último acceso al archivo mediante el **Navegador del IDE**, la lista de **Archivos activos** en el editor o el cuadro de diálogo **Windows**.

  El **Navegador del IDE** funciona como el conmutador de aplicaciones de Windows. No está disponible en los menús y solo se puede acceder a él mediante teclas de método abreviado. Puede usar uno de los dos comandos para acceder al **Navegador del IDE** (que se muestra a continuación) y desplazarse por los archivos, dependiendo del orden en el que quiere recorrerlos.

  ![Navegador del IDE de Visual Studio](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` le permite moverse al último archivo abierto y `Window.NextDocumentWindowNav` le permite moverse en el orden inverso. La configuración general de desarrollo asigna CTRL + MAYÚS + TAB a `Window.PreviousDocumentWindowNav` y CTRL + TAB a `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Si está usando un combinación de opciones que aún no tiene una combinación de teclas de método abreviado asignada, puede asignar su propio comando personalizado con la página **Teclado** del cuadro de diálogo **Opciones**. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Para cambiar a archivos concretos en el editor

-   Presione CTRL + TAB para mostrar el **Navegador del IDE**. Mantenga presionada la tecla CTRL y presione la tecla TAB varias veces hasta que seleccione el archivo al que desea cambiar.

    > [!TIP]
    >  Para invertir el orden por el que se desplaza por la lista **Archivos activos**, mantenga presionadas las teclas CTRL + MAYÚS y presione la tecla TAB.

     \- o -

-   En la esquina superior derecha del editor, pulse el botón **Archivos activos** y, después, seleccione en la lista un archivo al que cambiar.

     \- o -

-   En la barra de menús, pulse **Ventana**, **Windows**.

-   En la lista, seleccione el archivo que quiere ver y, después, pulse **Activar**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Navegar entre las ventanas de herramientas en el IDE
 El **Navegador del IDE** también permite recorrer las ventanas de herramientas que se encuentren abiertas en el IDE. Puede usar uno de los dos comandos para acceder al **Navegador del IDE** y desplazarse por las ventanas de herramientas, dependiendo del orden en el que quiere recorrerlos. `Window.PreviousToolWindowNav` le permite moverse al último archivo abierto y `Window.NextToolWindowNav` le permite moverse en el orden inverso. La configuración general de desarrollo asigna MAYÚS + ALT + F7 a `Window.PreviousDocumentWindowNav` y ALT + F7 a `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Si está usando un combinación de opciones que aún no tiene una combinación de teclas de método abreviado asignada, puede asignar su propio comando personalizado con la página **Teclado** del cuadro de diálogo **Opciones**. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Para cambiar a una ventana de herramientas específica en el IDE

-   Presione ALT + F7 para mostrar el **Navegador del IDE**. Mantenga presionada la tecla ALT y presione la tecla F7 varias veces hasta que seleccione la ventana a la que desea cambiar.

    > [!TIP]
    >  Para invertir el orden por el que se desplaza por la lista de **Ventanas de herramientas activas**, mantenga presionadas las teclas MAYÚS + ALT y presione la tecla F7.

## <a name="see-also"></a>Vea también
 [Personalizar los diseños de ventana](../ide/customizing-window-layouts-in-visual-studio.md) [métodos abreviados de teclado](../ide/default-keyboard-shortcuts-in-visual-studio.md)

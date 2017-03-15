---
title: "C&#243;mo: moverse por el IDE de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "documentos [Visual Studio], navegar"
  - "entornos [Visual Studio], navegación"
  - "archivos [Visual Studio], navegar entre"
  - "explorador del IDE"
  - "IDE, navegación"
  - "navegación [Visual Studio]"
  - "Window.NextDocumentWindowNav"
  - "ventanas [Visual Studio], navegar"
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# C&#243;mo: moverse por el IDE de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El entorno de desarrollo integrado \(IDE\) está diseñado para permitirle desplazarse de ventana en ventana y de archivo en archivo de varias maneras diferentes, dependiendo de sus preferencias o de los requisitos del proyecto.  Puede decidir recorrer en ciclo los archivos abiertos en el editor o todas las ventanas de herramientas activas en el IDE.  También puede cambiar directamente a cualquier archivo que esté abierto en el editor, sin tener en cuenta el orden en que se tuvo acceso en último lugar.  Estas características pueden ayudar a aumentar la productividad mientras se trabaja en el IDE.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos.  Esta página de Ayuda se ha redactado teniendo en cuenta la **Configuración general de desarrollo**.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Navegar entre archivos en el editor  
 Puede utilizar varios métodos para desplazarse por los archivos abiertos en el editor.  Puede desplazarse entre los archivos según el orden en el que tenga acceso a ella, utiliza el navegador del IDE para buscar rápidamente cualquier archivo abierto, o archivos favoritos del punto de conexión a la pestaña bien de modo que siempre estén visibles.  
  
 Puede navegar hacia atrás y hacia delante por los archivos abiertos en el editor basándose en el orden en el que se obtuvo acceso a ellos, como si usara los botones Atrás y Adelante para ver el historial en Microsoft Internet Explorer.  
  
#### Para desplazarse por los archivos abiertos por orden de uso  
  
-   Para activar los documentos abiertos en el orden de acceso más reciente, presione CTRL \+ ﻿SIGNO MENOS.  
  
-   Para activar los documentos abiertos en el orden inverso, presione CTRL \+ MAYÚS \+ ﻿SIGNO MENOS.  
  
    > [!NOTE]
    >  **Navegar hacia atrás** y **Navegar hacia delante** también se encuentran en el menú **Ver**.  
  
 También puede cambiar a un archivo concreto abierto en el editor, sin tener en cuenta la última vez que se obtuvo acceso al archivo, mediante el **Navegador del IDE**, la lista **Archivos activos** del editor o el cuadro de diálogo **Windows**.  
  
 El **Navegador del IDE** funciona de una forma muy parecida al conmutador de aplicaciones para Windows.  No está disponible en los menús y sólo se obtiene acceso a él por medio de teclas de método abreviado.  Existen dos comandos para obtener acceso al **Navegador del IDE** para recorrer en ciclo los archivos, y el más apropiado depende del orden en que desee recorrerlos.  `Window.PreviousDocumentWindowNav` permite desplazarse al archivo más reciente al que se obtuvo acceso y `Window.NextDocumentWindowNav` permite desplazarse en orden inverso.  Configuración general de desarrollo asigna CTRL \+ MAYÚS \+ TAB a `Window.PreviousDocumentWindowNav` y CTRL \+ TAB a `Window.NextDocumentWindowNav`.  
  
> [!NOTE]
>  Si en la combinación de valores de configuración que está utilizando aún no se ha asignado una combinación de teclas de método abreviado a este comando, puede asignar su propio comando personalizado en la página **Teclado** del cuadro de diálogo **Opciones**.  Para obtener más información, consulte [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
#### Para cambiar a archivos concretos en el editor  
  
-   Presione CTRL \+ TAB para mostrar el **Navegador del IDE**.  Mantenga presionada la tecla CTRL y presione repetidamente TAB hasta que esté seleccionado el archivo al que piense cambiar.  
  
    > [!TIP]
    >  Para invertir el orden en el que se recorre la lista **Archivos activos**, mantenga presionadas las teclas CTRL \+ MAYÚS y presione TAB.  
  
     \-O bien\-  
  
-   En la esquina superior derecha del editor, elija el botón de **Archivos activos** , y seleccione un archivo de la lista para cambiar.  
  
     \-O bien\-  
  
-   En la barra de menú, elija **Ventana**, **Ventanas**.  
  
-   En la lista, seleccione el archivo que desee ver y elegir **Activar**.  
  
## Navegar entre las ventanas de herramientas en el IDE  
 El **Navegador del IDE** también le permite recorrer en ciclo las ventanas de herramientas que estén abiertas en el IDE.  Existen dos comandos para obtener acceso al **Navegador del IDE** para recorrer en ciclo las ventanas de herramientas, y el más apropiado depende del orden en que desee recorrerlas.  `Window.PreviousToolWindowNav` permite desplazarse al archivo más reciente al que se obtuvo acceso y `Window.NextToolWindowNav` permite desplazarse en orden inverso.  Configuración general de desarrollo asigna MAYÚS \+ ALT \+ F7 a `Window.PreviousDocumentWindowNav` y ALT \+ F7 a `Window.NextDocumentWindowNav`.  
  
> [!NOTE]
>  Si en la combinación de valores de configuración que está utilizando aún no se ha asignado una combinación de teclas de método abreviado a este comando, puede asignar su propio comando personalizado en la página **Teclado** del cuadro de diálogo **Opciones**.  Para obtener más información, consulte [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
#### Para cambiar a una ventana de herramientas concreta en el IDE  
  
-   Presione ALT\+F7 para mostrar el **Navegador del IDE**.  Mantenga presionada la tecla ALT y presione repetidamente F7 hasta que esté seleccionada la ventana a la que piense cambiar.  
  
    > [!TIP]
    >  Para invertir el orden en que se recorre la lista **Ventanas de herramientas activas**, mantenga presionadas las teclas MAYÚS \+ ALT y presione F7.  
  
## Vea también  
 [Personalizar los diseños de ventana](../ide/customizing-window-layouts-in-visual-studio.md)   
 [Métodos abreviados de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md)
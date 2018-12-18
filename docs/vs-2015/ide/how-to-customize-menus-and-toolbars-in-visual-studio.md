---
title: 'Cómo: Personalizar menús y barras de herramientas en Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f7301a05ff17c20532a394fd1f26ab9fd98c3b65
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237892"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Cómo: Personalizar menús y barras de herramientas en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede personalizar Visual Studio no solo agregando y quitando barras de herramientas y menús de la barra de menús, sino agregando y quitando comandos de cualquier barra de herramientas o menú concreto.  
  
> [!WARNING]
>  Después de personalizar una barra de herramientas o un menú, asegúrese de que la casilla permanece seleccionada en el cuadro de diálogo **Personalizar**. De lo contrario, los cambios no se conservarán después de cerrar y volver a abrir Visual Studio.  
  
 **En este tema:**  
  
-   [Agregar, quitar o mover un menú de la barra de menús](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)  
  
-   [Agregar, quitar o mover una barra de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)  
  
-   [Personalizar un menú o una barra de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)  
  
-   [Restaurar un menú o una barra de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)  
  
##  <a name="bkmk_addmenu"></a> Agregar, quitar o mover un menú de la barra de menús  
  
1.  En la barra de menús, elija **Herramientas**, **Personalizar**.  
  
     Se abrirá el cuadro de diálogo **Personalizar**.  
  
2.  En la pestaña **Comandos**, deje el botón de opción **Barra de menús** seleccionado, deje **Barra de menús** seleccionado en la lista situada junto a esa opción y realice uno de los siguientes conjuntos de pasos:  
  
    -   Para agregar un menú, elija el botón **Add New Menu** (Agregar nuevo menú), elija el botón **Modificar selección** y escriba un nombre para el menú que quiere agregar.  
  
         ![Cuadro de diálogo Personalizar que muestra cómo agregar un menú](../ide/media/addmenu.png "AddMenu")  
  
    -   Para quitar un menú, selecciónelo en la lista **Controles** y elija el botón **Eliminar**.  
  
    -   Para mover un menú dentro de la barra de menús, seleccione el menú en la lista **Controles** y, después, elija el botón **Subir** o **Bajar**.  
  
##  <a name="bkmk_addtoolbar"></a> Agregar, quitar o mover una barra de herramientas  
  
1.  En la barra de menús, elija **Herramientas**, **Personalizar**.  
  
     Se abrirá el cuadro de diálogo **Personalizar**.  
  
2.  En la pestaña **Barra de herramientas**, realice uno de los siguientes conjuntos de pasos:  
  
    -   Para agregar una barra de herramientas, elija el botón **Nuevo**, especifique un nombre para la barra de herramientas que quiere agregar y, después, seleccione el botón **Aceptar**.  
  
         ![Cuadro de diálogo Personalizar que muestra cómo agregar una barra de herramientas](../ide/media/addtoolbar.png "AddToolbar")  
  
    -   Para quitar una barra de herramientas personalizada, selecciónela en la lista **Barras de herramientas** y, después, elija el botón **Eliminar**.  
  
        > [!IMPORTANT]
        >  Puede eliminar las barras de herramientas que haya creado pero no las predeterminadas.  
  
    -   Para mover una barra de herramientas a otra ubicación de acoplamiento, selecciónela en la lista **Barras de herramientas**, elija el botón **Modificar selección** y elija una ubicación en la lista que aparece.  
  
         También puede arrastrar una barra de herramientas por el borde izquierdo para moverla a cualquier parte del área de acoplamiento principal.  
  
        > [!NOTE]
        >  Para obtener más información sobre cómo mejorar el uso y la accesibilidad de las barras de herramientas, vea [Cómo: Establecer opciones de accesibilidad de IDE](../ide/reference/how-to-set-ide-accessibility-options.md).  
  
##  <a name="bkmk_customize"></a> Personalizar un menú o una barra de herramientas  
  
1.  En la barra de menús, elija **Herramientas**, **Personalizar**.  
  
     Se abrirá el cuadro de diálogo **Personalizar**.  
  
2.  En la pestaña **Comandos**, elija el botón de opción del tipo de elemento que quiere personalizar.  
  
3.  En la lista de ese tipo de elemento, elija el menú o la barra de herramientas que desea personalizar y después realice uno de los siguientes conjuntos de pasos:  
  
    -   Para agregar un comando, elija el botón **Agregar comando**.  
  
         En el cuadro de diálogo **Agregar comando**, elija un elemento de la lista **Categorías**, un elemento de la lista **Comandos** y el botón **Aceptar**.  
  
         ![Cuadro de diálogo Agregar comando en Visual Studio](../ide/media/addcommand.png "AddCommand")  
  
    -   Para eliminar un comando, selecciónelo en la lista **Controles** y elija el botón **Eliminar**.  
  
    -   Para reordenar los comandos, seleccione un comando de la lista **Controles** y elija el botón **Subir** o **Bajar**.  
  
    -   Para separar los comandos en grupos, elija un comando de la **controles** lista, elija el **Modificar selección** botón y, a continuación, elija **comenzar un grupo** en el menú que aparece.  
  
##  <a name="bkmk_reset"></a> Restaurar un menú o una barra de herramientas  
  
1.  En la barra de menús, elija **Herramientas**, **Personalizar**.  
  
     Se abrirá el cuadro de diálogo **Personalizar**.  
  
2.  En la pestaña **Comandos**, elija el botón de opción del tipo de elemento que quiere restablecer.  
  
3.  En la lista de ese tipo de elemento, elija el menú o la barra de herramientas que desea restaurar.  
  
4.  Elija el botón **Modificar selección** y seleccione **Restablecer** en el menú que aparece.  
  
     También puede restablecer todos los menús y barras de herramientas mediante el botón **Restablecer todo**.




---
title: Pantalla completa de Visual Studio y modo de espacio virtual | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0f6535c656c512d5c849a8a5d8d2fb37319aa883
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-manage-editor-modes"></a>Procedimiento para administrar los modos del editor
Puede mostrar el editor de código de Visual Studio en varios modos de visualización.  
  
> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en este artículo, en función de los valores de configuración o de edición activos. Para cambiar la configuración, por ejemplo, a la configuración **General** o **Visual C++**, elija **Herramientas**, **Importar y exportar configuraciones** y, después, elija **Restablecer todas las configuraciones**.
  
## <a name="enabling-full-screen-mode"></a>Habilitar el modo de pantalla completa  
Puede decidir ocultar todas las ventanas de herramientas y ver solo las ventanas de documento habilitando el modo **Pantalla completa**.  
  
#### <a name="to-enable-full-screen-mode"></a>Para habilitar el modo de pantalla completa  
  
-   Presione **Alt**+**Mayús**+**Entrar** para entrar o salir del modo **Pantalla completa**.  
  
     O bien  
  
-   Ejecute el comando `View.Fullscreen` en la ventana **Comandos**.  
  
## <a name="enabling-virtual-space-mode"></a>Habilitar el modo de espacio virtual  
En el modo de **espacio virtual**, los espacios se insertan al final de cada línea de código. Seleccione esta opción para colocar los comentarios en una posición coherente al lado del código.  
  
#### <a name="to-enable-virtual-space-mode"></a>Para habilitar el modo de espacio virtual  
  
1.  Seleccione **Opciones** en el menú **Herramientas**.

2.  Expanda la carpeta **Editor de texto** y pulse **Todos los lenguajes** para establecer esta opción globalmente, o pulse una carpeta de lenguaje específica. (Por ejemplo, para activar los números de línea solo en Visual Basic, elija los nodos Básico, Editor de texto).
  
3.  Seleccione las opciones **General** y en **Configuración**, seleccione **Habilitar espacio virtual**.  
  
    > [!NOTE]
    >  **Espacio virtual** está habilitado en el modo **Selección de columnas**. Cuando el modo **Espacio virtual** no está habilitado, el punto de inserción se mueve desde el final de una línea directamente al primer carácter de la siguiente.  
  
## <a name="see-also"></a>Vea también
[Personalizar el editor](../ide/customizing-the-editor.md)   
[Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)   
[Fuentes y colores, Entorno, Opciones (Cuadro de diálogo)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
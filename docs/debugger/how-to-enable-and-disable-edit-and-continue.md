---
title: "Cómo: habilitar y deshabilitar Editar y continuar (C#, VB, C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1c00546b983c9bbb0fd6c01717bd0a09c993e11b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Cómo: habilitar y deshabilitar Editar y continuar (C#, VB, C++)
Puede deshabilitar o Habilitar Editar y continuar en la **opciones** cuadro de diálogo en tiempo de diseño. No puede cambiar este valor mientras esté depurando.  
  
Editar y continuar solo funciona en las compilaciones de depuración. En C++ nativo, Editar y continuar requiere el uso de la opción /INCREMENTAL. Para obtener más información sobre los requisitos de características de C++, vea este [entrada de blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) y [editar y continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar o deshabilitar Editar y continuar  
  
1.  Si está en una sesión de depuración, detenga la depuración (**MAYÚS + F5**).

2.  Abrir página de opciones de depuración (**Herramientas > Opciones > depuración**).
  
3.  Seleccione **General**y desplácese hacia abajo hasta **editar y continuar** categoría (panel derecho).  
  
4.  Para habilitar, seleccione la **Habilitar Editar y continuar** casilla de verificación. Para deshabilitarla, desactive la casilla.  
  
    > [!NOTE]
    >  Si se habilita IntelliTrace y se recopilan eventos de IntelliTrace e información de llamadas, se deshabilita Editar y continuar. Para obtener más información, consulte [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Para habilitar, seleccione **Habilitar Editar y continuar nativa**. Para deshabilitarla, desactive la casilla.

6. (C++) Establecer opciones adicionales para el código nativo.

    - **Aplicar cambios al continuar (solo nativo)**  
        Al continuar el proceso desde un estado de interrupción, Visual Studio compila y aplica los cambios de código pendientes realizados automáticamente. Si no está seleccionada, puede aplicar los cambios con el elemento "Aplicar cambios en el código" en el menú Depurar.  
  
    - **Avisar cuando haya código obsoleto (solo nativo)**  
        Obtenga advertencias sobre código obsoleto. 
  
7.  Haga clic en **Aceptar**.    
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar](../debugger/edit-and-continue.md)
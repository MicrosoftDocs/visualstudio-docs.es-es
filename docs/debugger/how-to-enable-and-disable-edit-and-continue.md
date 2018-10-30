---
title: 'Cómo: habilitar y deshabilitar Editar y continuar (C#, VB, C++) | Microsoft Docs'
ms.custom: ''
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: f0bf354f64be9c03a64beadcffdd7ff1138218df
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382757"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Cómo: habilitar y deshabilitar Editar y continuar (C#, VB, C++)

Puede deshabilitar o habilitar **editar y continuar** en Visual Studio **opciones** cuadro de diálogo en tiempo de diseño. **Editar y continuar** compilaciones funciona solo en modo de depuración. Para obtener más información, consulte [editar y continuar](../debugger/edit-and-continue.md). 
  
En C++ nativo, **editar y continuar** requiere el uso de la `/INCREMENTAL` opción. Para obtener más información sobre los requisitos de características en C++, vea este [entrada de blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) y [editar y continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
**Para habilitar o deshabilitar Editar y continuar:**  
  
1.  Si está en una sesión de depuración, detenga la depuración (**depurar** > **Detener depuración** o **MAYÚS**+**F5**) .

1.  En **herramientas** > **opciones** > (o **depurar** > **opciones**) > **depuración**  >  **General**, seleccione **editar y continuar** en el panel derecho.  
  
    > [!NOTE]
    >  Si se habilita IntelliTrace y se recopilan eventos de IntelliTrace e información de llamadas, se deshabilita Editar y continuar. Para obtener más información, consulte [IntelliTrace](../debugger/intellitrace.md).
    
1.  Para el código de C++, asegúrese de que **Habilitar Editar y continuar nativa** esté seleccionada y establecer las opciones adicionales:
    - **Aplicar cambios al continuar (solo nativo)**  
      
      Si selecciona esta opción, Visual Studio se compila automáticamente y aplica los cambios de código al continuar la depuración desde un estado de interrupción. En caso contrario, puede elegir aplicar los cambios con **depurar** > **aplicar cambios de código**.  
      
    - **Advertir sobre código obsoleto (solo nativo)**  
      
      Si se selecciona, ofrece las advertencias sobre código obsoleto. 
  
1.  Haga clic en **Aceptar**.    

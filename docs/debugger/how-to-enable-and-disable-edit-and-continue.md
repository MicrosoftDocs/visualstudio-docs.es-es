---
title: 'Cómo: habilitar y deshabilitar editar y continuar | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
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
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430538"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Cómo: habilitar y deshabilitar editar y continuar (C#, VB C++)

Puede deshabilitar o habilitar **Editar y continuar** en el cuadro de diálogo **Opciones** de Visual Studio en tiempo de diseño. **Editar y continuar** solo funciona en las compilaciones de depuración. Para obtener más información, vea [Editar y continuar](../debugger/edit-and-continue.md).

En el C++caso de Native, **Editar y continuar** requiere el uso de la opción `/INCREMENTAL`. Para obtener más información sobre los requisitos C++de características en, consulte esta [entrada de blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) y [Editar yC++continuar ()](../debugger/edit-and-continue-visual-cpp.md).

**Para habilitar o deshabilitar editar y continuar:**

1. Si está en una sesión de depuración, detenga la depuración (**Depurar**  > **detener depuración** o **MAYÚS** +**F5**).

1. En **herramientas**  > **Opciones** > (o **depurar** **Opciones**de  > ) > **depuración**  > **General**, seleccione **Editar y continuar** en el panel derecho.

    > [!NOTE]
    > Si se habilita IntelliTrace y se recopilan eventos de IntelliTrace e información de llamadas, se deshabilita Editar y continuar. Para obtener más información, vea [IntelliTrace](../debugger/intellitrace.md).

1. En C++ el código, asegúrese de que la opción Habilitar la opción **Editar y continuar nativa** está seleccionada y establezca las opciones adicionales:
    - **Aplicar cambios al continuar (solo nativo)**

      Si está seleccionada, Visual Studio compila y aplica automáticamente los cambios en el código al continuar la depuración desde un estado de interrupción. De lo contrario, puede elegir aplicar los cambios mediante **Depurar**  > **aplicar cambios de código**.

    - **Advertir sobre el código obsoleto (solo nativo)**

      Si se selecciona, proporciona advertencias sobre el código obsoleto.

1. Haga clic en **Aceptar**.

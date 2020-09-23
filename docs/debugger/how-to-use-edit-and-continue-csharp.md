---
title: para usar Editar y continuar (C#) | Microsoft Docs
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18d11f552d486fd9ebd7a95323e327324de14108
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851858"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedimiento Usar Editar y continuar (C#)
Con Editar y continuar, puede realizar y aplicar cambios en el código en modo de interrupción durante la depuración, sin tener que detener y reiniciar la sesión de depuración.

En C#, Editar y continuar se ejecuta automáticamente cuando se realizan cambios en modo de interrupción y, después, se continúa la depuración mediante **Continuar**, **Paso** o **Establecer instrucción siguiente**, o bien se evalúa una función en una ventana del depurador.

Para obtener más información, vea [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Editar y continuar no se admite para el código de integración optimizado, mixto o de SQL Server Common Language Runtime (CLR). Para obtener información sobre otros escenarios no admitidos, vea [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md). Si prueba Editar y continuar con uno de estos escenarios, aparecerá un cuadro de mensaje en el que se indica que no se admite.

**Para habilitar o deshabilitar Editar y continuar:**

1. Si está en una sesión de depuración, detenga la depuración (**Depurar** > **Detener depuración** o **Mayús**+**F5**).

1. En **Herramientas** > **Opciones** (o **Depurar** > **Opciones**) > **Depuración** > **General**, active o desactive la casilla **Habilitar Editar y continuar**.

La configuración tendrá efecto cuando se inicie o reinicie la sesión de depuración.

**Para usar Editar y continuar:**

1. Durante la depuración, en el modo de interrupción, realice un cambio en el código fuente.

1. En el menú **Depurar**, haga clic en **Continuar**, **Paso** o **Establecer instrucción siguiente** o evalúe una función en una ventana del depurador.

   La depuración continúa con el nuevo código compilado.

La opción Editar y continuar no admite algunos tipos de cambios del código. Para obtener más información, vea [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).

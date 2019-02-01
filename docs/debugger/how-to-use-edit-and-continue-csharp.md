---
title: Procedimiento Usar Editar y continuar (C#) | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
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
ms.openlocfilehash: ca4d8efda78974be00973ef3f6c5adcc77c2465d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965281"
---
# <a name="how-to-use-edit-and-continue-c"></a>Filtrar Usar Editar y continuar (C#)
Con Editar y continuar, puede realizar y aplicar los cambios en el código en modo de interrupción durante la depuración, sin tener que detener y reiniciar la sesión de depuración.  

Editar y continuar para C# lleva a cabo automáticamente cuando realice cambios en el código en modo de interrupción y luego continuar con la depuración mediante el uso de **continuar**, **paso**, o **Establecer instrucción siguiente**, o evaluar una función en una ventana del depurador.  

Para obtener más información, consulte [editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Editar y continuar no se admite para optimizado, combinar, o código de integración de SQL Server common language runtime (CLR). Para obtener información sobre otros escenarios no admitidos, vea [admite cambios de código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md). Si se intenta editar y continuar con uno de estos escenarios, aparece un cuadro de mensaje que indica que no se admite Editar y continuar.  
  
**Para habilitar o deshabilitar Editar y continuar:**  
   
1. Si está en una sesión de depuración, detenga la depuración (**depurar** > **Detener depuración** o **MAYÚS**+**F5**) .
   
1. En **herramientas** > **opciones** (o **depurar** > **opciones**) > **depuración**  >  **General**, active o desactive el **Habilitar Editar y continuar** casilla de verificación.  
  
La configuración surte efecto cuando se inicie o reinicie la sesión de depuración.  

**Para utilizar editar y continuar:**  
   
1. Durante la depuración en modo de interrupción, realizar un cambio en el código fuente.  
   
1. En el menú **Depurar**, haga clic en **Continuar**, **Paso** o **Establecer instrucción siguiente** o evalúe una función en una ventana del depurador.  
   
   Depuración continuará con el código compilado de nuevo. 

No se admiten algunos tipos de cambios de código por editar y continuar. Para obtener más información, consulte [admite cambios de código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).   

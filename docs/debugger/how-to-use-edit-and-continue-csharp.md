---
title: 'Cómo: utilizar editar y continuar (C#) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a1f073d401ddc1a99e365245f2a8c1b66b13fb8a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-edit-and-continue-c"></a>Cómo: Utilizar Editar y continuar (C#)
Con Editar y continuar para C#, puede realizar cambios en el código en modo de interrupción mientras depura. Los cambios pueden aplicarse sin necesidad de detener y reiniciar la sesión de depuración.  
  
 Editar y continuar se invoca automáticamente cuando se realizan cambios en modo de interrupción, y luego elija una ejecución del depurador comando, como **continuar**, **paso**, o **Establecer instrucción siguiente**, o evaluar una función en una ventana del depurador.  
  
> [!NOTE]
>  No se admite Editar y continuar al depurar optimiza el código, código mixto nativo/administrado o código de integración de SQL Server common language runtime (CLR). Para obtener información sobre otros escenarios no admitidos, vea [cambios admitidos en el código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md). Si se intenta aplicar cambios de código en alguno de estos escenarios, las pantallas de depurador un cuadro de diálogo cuadro que explica que editar y continuar no se admite.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Para invocar automáticamente Editar y continuar  
  
1.  En el modo de interrupción, realice un cambio en el código fuente.  
  
2.  Desde el **depurar** menú, haga clic en **continuar**, **paso**, o **Establecer instrucción siguiente** o evaluar una función en una ventana del depurador.  
  
     El código nuevo se compilará y la depuración se reanudará con el código nuevo. La opción Editar y continuar no admite algunos cambios. Para obtener más información, consulte [cambios admitidos en el código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar o deshabilitar Editar y continuar  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, expanda el **depuración** nodo y seleccione **editar y continuar**.  
  
3.  En el **opciones** cuadro de diálogo **editar y continuar** página, active o desactive el **Habilitar Editar y continuar** casilla de verificación.  
  
     La configuración tendrá efecto cuando se reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Cambios admitidos en el código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md)   
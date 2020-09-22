---
title: Procedimiento para usar Editar y continuar (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842807"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedimiento Usar Editar y continuar (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con Editar y continuar para C#, puede realizar cambios en el código en modo de interrupción mientras depura. Los cambios pueden aplicarse sin necesidad de detener y reiniciar la sesión de depuración.  
  
 Editar y continuar se invoca automáticamente al realizar cambios en modo de interrupción y, a continuación, elegir un comando de ejecución del depurador, como **continuar**, **paso**o **Establecer instrucción siguiente**, o evaluar una función en una ventana del depurador.  
  
> [!NOTE]
> No se admite Editar y continuar cuando se depura código de Compact Framework, código optimizado, código mixto nativo/administrado o código de integración de Common Language Runtime (CLR) de SQL Server. En caso de que se intenten aplicar cambios en el código en alguno de estos escenarios, el depurador mostrará un cuadro de diálogo donde se explique que no se admite la opción Editar y continuar.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Para invocar automáticamente Editar y continuar  
  
1. En el modo de interrupción, realice un cambio en el código fuente.  
  
2. En el menú **depurar** , haga clic en **continuar**, **paso**o **Establecer instrucción siguiente** o en evaluar una función en una ventana del depurador.  
  
     El código nuevo se compilará y la depuración se reanudará con el código nuevo. La opción Editar y continuar no admite algunos cambios. Para obtener más información, consulte [cambios admitidos en el código (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar o deshabilitar Editar y continuar  
  
1. En el menú **Herramientas** , haga clic en **Opciones**.  
  
2. En el cuadro de diálogo **Opciones** , expanda el nodo **depuración** y seleccione **Editar y continuar**.  
  
3. En la página **Editar y continuar** del cuadro de diálogo **Opciones** , Active o desactive la casilla **Habilitar editar y continuar** .  
  
     La configuración tendrá efecto cuando se reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Consulte también  
 [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Cambios de código admitidos (C#)](../debugger/supported-code-changes-csharp.md)   
 [Errores y advertencias de editar y continuar (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)

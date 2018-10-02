---
title: 'Cómo: utilizar editar y continuar (C#) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4305c39c62dfcc927ea7295ceec786d3da40f56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576540"
---
# <a name="how-to-use-edit-and-continue-c"></a>Cómo: Utilizar Editar y continuar (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: utilizar editar y continuar (C#)](https://docs.microsoft.com/visualstudio/debugger/how-to-use-edit-and-continue-csharp).  
  
Con Editar y continuar para C#, puede realizar cambios en el código en modo de interrupción mientras depura. Los cambios pueden aplicarse sin necesidad de detener y reiniciar la sesión de depuración.  
  
 Editar y continuar se invoca automáticamente cuando realice cambios en el modo de interrupción y luego elija una ejecución del depurador comando, como **continuar**, **paso**, o **Establecer instrucción siguiente**, o evaluar una función en una ventana del depurador.  
  
> [!NOTE]
>  No se admite Editar y continuar cuando se depura código de Compact Framework, código optimizado, código mixto nativo/administrado o código de integración de Common Language Runtime (CLR) de SQL Server. En caso de que se intenten aplicar cambios en el código en alguno de estos escenarios, el depurador mostrará un cuadro de diálogo donde se explique que no se admite la opción Editar y continuar.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Para invocar automáticamente Editar y continuar  
  
1.  En el modo de interrupción, realice un cambio en el código fuente.  
  
2.  Desde el **depurar** menú, haga clic en **continuar**, **paso**, o **Establecer instrucción siguiente** o evaluar una función en una ventana del depurador.  
  
     El código nuevo se compilará y la depuración se reanudará con el código nuevo. La opción Editar y continuar no admite algunos cambios. Para obtener más información, consulte [Supported Code Changes (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar o deshabilitar Editar y continuar  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, expanda el **depuración** nodo y seleccione **editar y continuar**.  
  
3.  En el **opciones** cuadro de diálogo **editar y continuar** página, active o desactive el **Habilitar Editar y continuar** casilla de verificación.  
  
     La configuración tendrá efecto cuando se reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Cambios admitidos en el código (C#)](../debugger/supported-code-changes-csharp.md)   
 [Errores y advertencias de Editar y continuar (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)




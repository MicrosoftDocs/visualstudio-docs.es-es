---
title: Errores y advertencias de editar y continuarC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eec40bc584e831f8b43b79c9bc7cee5a48a291aa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850973"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Errores y advertencias de Editar y continuar (C#)
Ha realizado una edición en una sección de código que no se permite en Editar y continuar de Visual C#.  
  
 La característica Editar y continuar de [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] permite detener la ejecución del programa en el modo de interrupción, realizar cambios en el código en ejecución y, a continuación, reanudar la ejecución del programa con estos nuevos cambios incorporados.  
  
 Las modificaciones del código declarativo que afectan a la estructura pública de una clase suelen estar prohibidas, y no se permiten algunas modificaciones que se podrían hacer en un método, cuerpo de propiedad o declaraciones privadas en una clase. Siempre que es posible, Editar y continuar marca el código que no se puede editar en gris claro y muestra un mensaje de error.  
  
 Para obtener más información sobre las ediciones compatibles con la característica Editar y continuar de [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], vea [Supported Code Changes (C#)](../debugger/supported-code-changes-csharp.md). Si necesita más información sobre una advertencia o error específico, puede buscar o publicar en el [foro de IDE de Visual C#](https://social.msdn.microsoft.com/Forums/en-US/csharpide/threads)de MSDN.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1. En el menú **Depurar** , elija **Deshacer** para deshacer el cambio.  
  
     O bien,  
  
2. Detenga la sesión de depuración, realice las tareas de edición e inicie una nueva sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

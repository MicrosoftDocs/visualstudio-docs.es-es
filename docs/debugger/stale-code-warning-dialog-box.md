---
title: Obsoleto el cuadro de diálogo de advertencia de código | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e212602b317127cfd14adcd246a23cdd92ed86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281798"
---
# <a name="stale-code-warning-dialog-box"></a>Advertencia de código obsoleto (cuadro de diálogo)
Este cuadro de diálogo aparece cuando han realizado cambios a código nativo de código que **editar y continuar** no se pudo aplicar inmediatamente. Por tanto, parte del código nativo en el marco de pila actual no está actualizado, es decir, que está obsoleto. Para obtener más información, consulte [Cómo: trabajar con código obsoleto](/visualstudio/debugger/edit-and-continue-visual-cpp#bkmk_how_to_work_with_stale_code).  
  
 **No volver a mostrar este cuadro de diálogo**  
 Si activa esta casilla, la función Editar y continuar aplicará los cambios en el código sin pedir permiso en el futuro. Puede activar esta advertencia de nuevo, vaya a la **opciones** cuadro de diálogo, abra el **depuración** carpeta, haga clic en el **editar y continuar** página y seleccionar **Avisar cuando haya código obsoleto**.  
  
## <a name="see-also"></a>Vea también  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)   
 [Editar y continuar, Depuración, Opciones (Cuadro de diálogo)](/visualstudio/debugger/edit-and-continue)
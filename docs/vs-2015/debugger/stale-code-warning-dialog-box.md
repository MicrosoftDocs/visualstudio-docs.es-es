---
title: Obsoleto el cuadro de diálogo de advertencia de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adb8bfdf5edb4f6aa04a53f051fafa9ef3793e10
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999419"
---
# <a name="stale-code-warning-dialog-box"></a>Advertencia de código obsoleto (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando se han realizado cambios en el código nativo que **Editar y continuar** no pudo aplicar inmediatamente. Por tanto, parte del código nativo en el marco de pila actual no está actualizado, es decir, que está obsoleto. Para obtener más información, vea [Cómo: Trabajar con código obsoleto](http://msdn.microsoft.com/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **No volver a mostrar este cuadro de diálogo**  
 Si activa esta casilla, la función Editar y continuar aplicará los cambios en el código sin pedir permiso en el futuro. Para volver a activar esta advertencia, vaya al cuadro de diálogo **Opciones**, abra la carpeta **Depuración**, haga clic en la página **Editar** y continuar y seleccione **Avisar cuando haya código obsoleto**.  
  
## <a name="see-also"></a>Vea también  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)   
 [Editar y continuar, Depuración, Opciones (Cuadro de diálogo)](http://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103)

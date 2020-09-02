---
title: Advertencia de código obsoleto (cuadro de diálogo) | Microsoft Docs
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
ms.openlocfilehash: a89738446bf8c08680835ddccb7efa30c2f740f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694696"
---
# <a name="stale-code-warning-dialog-box"></a>Advertencia de código obsoleto (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando se han realizado cambios en el código nativo que **Editar y continuar** no pudo aplicar inmediatamente. Por tanto, parte del código nativo en el marco de pila actual no está actualizado, es decir, que está obsoleto. Para obtener más información, consulte [Cómo: trabajar con código obsoleto](https://msdn.microsoft.com/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **No volver a mostrar este cuadro de diálogo**  
 Si activa esta casilla, la función Editar y continuar aplicará los cambios en el código sin pedir permiso en el futuro. Para volver a activar esta advertencia, vaya al cuadro de diálogo **Opciones**, abra la carpeta **Depuración**, haga clic en la página **Editar** y continuar y seleccione **Avisar cuando haya código obsoleto**.  
  
## <a name="see-also"></a>Consulte también  
 [Cambios de código admitidos (C++)](../debugger/supported-code-changes-cpp.md)   
 [Editar y continuar, Depuración, Opciones (Cuadro de diálogo)](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103)

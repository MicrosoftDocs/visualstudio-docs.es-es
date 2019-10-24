---
title: Cuadro de diálogo Advertencia de código obsoleto | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dba38e5b5d9f7a2be710cad58d6f2297dd03a412
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729539"
---
# <a name="stale-code-warning-dialog-box"></a>Advertencia de código obsoleto (cuadro de diálogo)

Este cuadro de diálogo aparece cuando se han realizado cambios en el código nativo que **Editar y continuar** no pudo aplicar inmediatamente. Por tanto, parte del código nativo en el marco de pila actual no está actualizado, es decir, que está obsoleto. Para más información, consulte [Editar y continuar (C++)](edit-and-continue-visual-cpp.md).

**No volver a mostrar este cuadro de diálogo**

Si activa esta casilla, la función Editar y continuar aplicará los cambios en el código sin pedir permiso en el futuro. Para volver a activar esta advertencia, vaya al cuadro de diálogo **Opciones**, abra la carpeta **Depuración**, haga clic en la página **Editar** y continuar y seleccione **Avisar cuando haya código obsoleto**.

## <a name="see-also"></a>Vea también

- [Cambios admitidos en el código (C++)](supported-code-changes-cpp.md)
- [Editar y continuar, Depuración, Opciones (Cuadro de diálogo)](edit-and-continue.md)
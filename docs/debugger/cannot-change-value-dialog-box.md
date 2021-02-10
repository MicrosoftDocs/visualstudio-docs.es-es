---
title: Cuadro de diálogo No se puede cambiar el valor | Microsoft Docs
description: Revise el cuadro de diálogo No se puede cambiar el valor, el cual aparece en Visual Studio si intenta cambiar una variable a un valor no válido en una ventana del depurador o en Inspección rápida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3dfedc12a1634e6f804c0cb3a9fceee9e9d43216
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857895"
---
# <a name="cannot-change-value-dialog-box"></a>Cuadro de diálogo No se puede cambiar el valor
## <a name="error"></a>Error
 `The value of this variable cannot be changed` &#124; `The name` *nombre* `does not exist in the current context` &#124; *otros mensajes*

 Este cuadro de mensaje aparece al intentar cambiar el contenido de una variable a un valor no válido en una ventana del depurador (ventanas Automático, Inspección o Variables locales) o en el cuadro de diálogo Inspección rápida. Por ejemplo, este cuadro de mensaje aparece si intenta establecer el valor de una variable entera a una cadena de caracteres.

## <a name="solution"></a>Soluciones
 Asegúrese de que el valor de entrada que escribe en la ventana del depurador o en el cuadro de diálogo Inspección rápida representa un valor válido para la variable que está intentando establecer.

## <a name="see-also"></a>Vea también

- [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)
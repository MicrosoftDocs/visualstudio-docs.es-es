---
title: Dónde buscar códigos de error de Win32 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebd2b4dd65fbcb957e13207cc5550a10b7870219
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699241"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Dónde buscar códigos de error de Win32
El archivo WINERROR.H, situado en el directorio INCLUDE de la instalación predeterminada del sistema, contiene las definiciones de código de error para las funciones de la API Win32.

 Puede buscar un código de error escribiendo el código en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**. Por ejemplo:

`0x80000004,hr`


## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
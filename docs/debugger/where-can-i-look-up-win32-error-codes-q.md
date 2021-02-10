---
title: Dónde buscar códigos de error de Win32 | Microsoft Docs
description: Para buscar un código de error de Win32, escríbalo en Inspección o en Inspección rápida. Por ejemplo, "0x80000004,hr". Las definiciones de los códigos de error se encuentran en INCLUDE\WINERROR.H.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4eb61a6eda5848277a1da95f9282b396b413ad5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883836"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Dónde buscar códigos de error de Win32
El archivo WINERROR.H, situado en el directorio INCLUDE de la instalación predeterminada del sistema, contiene las definiciones de código de error para las funciones de la API Win32.

 Puede buscar un código de error escribiendo el código en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**. Por ejemplo:

`0x80000004,hr`

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
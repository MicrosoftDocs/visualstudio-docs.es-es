---
title: Editar y continuar (Visual C#) | Microsoft Docs
description: Editar y continuar está disponible para los proyectos de Visual C#. Obtenga información sobre qué ediciones se admiten y cómo puede controlar si se aplican y cuándo.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 375e1db598f925a193def159203ccb7e5c5fdf05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871863"
---
# <a name="edit-and-continue-visual-c"></a>Editar y continuar (Visual C#)
 Con Editar y continuar para C#, puede realizar cambios en el código en modo de interrupción mientras depura. Los cambios pueden aplicarse sin necesidad de detener y reiniciar la sesión de depuración. En modo de ejecución, el editor de código fuente es de solo lectura.

 Editar y continuar admite la mayoría de los cambios que podría realizar durante una sesión de depuración, pero existen algunas excepciones. Para obtener más información, vea [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Editar y continuar es compatible con UWP en Windows 10 y aplicaciones x86 y x64 que tienen como destino el escritorio de .NET Framework 4.6 o versiones posteriores (.NET Framework es solo una versión de escritorio).

 > [!NOTE]
 > Las aplicaciones y plataformas no compatibles incluyen Silverlight 5 y Windows 8.1.

 Si se habilita Editar y continuar, los cambios admitidos se aplican automáticamente cuando se utiliza un comando de ejecución del depurador, como **Continuar**, **Paso**, **Establecer instrucción siguiente**, o cuando se realiza una evaluación de función en una ventana del depurador.

 Para obtener más información, vea [Cómo: Uso de Editar y continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Vea también
- [Cómo: Uso de Editar y continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Escritura y depuración de código XAML en ejecución con Recarga activa de XAML en Visual Studio](../xaml-tools/xaml-hot-reload.md)

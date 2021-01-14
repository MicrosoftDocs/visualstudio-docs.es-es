---
title: Sugerencias para depurar subprocesos en código nativo | Microsoft Docs
description: Lea una lista de sugerencias para depurar subprocesos en código nativo si va a depurar aplicaciones multiproceso en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150059"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Sugerencias para depurar subprocesos en código nativo
A continuación se muestran algunas sugerencias que puede usar al depurar subprocesos en código nativo:

- Puede ver el contenido del Bloque de información de subprocesos escribiendo `@TIB` en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**.

- Puede ver el último código de error del subproceso actual escribiendo `@Err` en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**.

- Las funciones de las bibliotecas en tiempo de ejecución de C (CRT) pueden ser útiles para depurar una aplicación multiproceso. Para obtener más información, consulte [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
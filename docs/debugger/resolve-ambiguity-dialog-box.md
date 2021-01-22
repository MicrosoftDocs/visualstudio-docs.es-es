---
title: Resolver ambigüedad (cuadro de diálogo) | Microsoft Docs
description: Consulte el cuadro de diálogo de Visual Studio Resolver ambigüedad, que se muestra cuando el depurador no puede elegir la ubicación que se debe mostrar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6f7156a43bc8c5c60415680b4380600e9e695cc
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205611"
---
# <a name="resolve-ambiguity-dialog-box"></a>Resolver ambigüedad (cuadro de diálogo)
El cuadro de diálogo `Resolve Ambiguity` aparece cuando el depurador no puede elegir qué ubicación va a mostrar. Por ejemplo, si utiliza plantillas de C++, puede crear varias funciones a partir de una única plantilla de función. Si el depurador se detiene en una ubicación del código fuente de la plantilla, y elige `Go To Disassembly`, el depurador ofrece varias opciones. Cada función creada a partir de la plantilla tiene su propio código de desensamblado, y el depurador no sabe qué código es el que debe mostrar. El cuadro de diálogo `Resolve Ambiguity` permite seleccionar la ubicación deseada en una lista con todas las ubicaciones correspondientes.

 `Choose the specific location` Enumera todas las ubicaciones correspondientes del comando.

 `Address` Muestra las direcciones de memoria de cada función.

 `Function` Muestra el nombre de cada función.

 `Module` Muestra el módulo (EXE o DLL) que contiene el código objeto de la función.

## <a name="see-also"></a>Vea también
- [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)
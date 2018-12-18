---
title: Resolver ambigüedad cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13458279d1970bd1b398a0de6e74b34b0b3a99a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807594"
---
# <a name="resolve-ambiguity-dialog-box"></a>Resolver ambigüedad (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El cuadro de diálogo `Resolve Ambiguity` aparece cuando el depurador no puede elegir qué ubicación va a mostrar. Por ejemplo, si utiliza plantillas de C++, puede crear varias funciones a partir de una única plantilla de función. Si el depurador se detiene en una ubicación del código fuente de la plantilla, y elige `Go To Disassembly`, el depurador ofrece varias opciones. Cada función creada a partir de la plantilla tiene su propio código de desensamblado, y el depurador no sabe qué código es el que debe mostrar. El cuadro de diálogo `Resolve Ambiguity` permite seleccionar la ubicación deseada en una lista con todas las ubicaciones correspondientes.  
  
 `Choose the specific location`  
 Enumera todas las ubicaciones correspondientes del comando.  
  
 `Address`  
 Muestra las direcciones de memoria de cada función.  
  
 `Function`  
 Muestra el nombre de cada función.  
  
 `Module`  
 Muestra el módulo (EXE o DLL) que contiene el código objeto de la función.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)




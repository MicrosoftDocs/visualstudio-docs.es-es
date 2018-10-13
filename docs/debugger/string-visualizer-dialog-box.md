---
title: Ver cadenas en un visualizador de cadenas | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 689889e98a5a9b69a49e73ccea73f30fc3c25249
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274318"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Ver cadenas en un visualizador de cadenas en Visual Studio

Durante la depuración en Visual Studio, puede ver las cadenas con el visualizador de cadenas integrada. El visualizador de cadenas muestra las cadenas que son demasiado grandes para una ventana de sugerencia o depurador de datos. También puede ayudarle a identificar cadenas con formato incorrecto.

El visualizador de cadenas integrada incluye texto sin formato, XML, HTML y JSON opciones. Visualizadores para otros tipos, tales como objetos WPF, también se pueden abrir desde el **automático** u otras ventanas del depurador.

## <a name="open-a-string-visualizer"></a>Abrir un visualizador de cadenas

Para abrir el visualizador de cadenas, debe ponerse en pausa durante la depuración. Mantenga el mouse sobre una variable que tiene un texto sin formato, XML, HTML o JSON el valor de cadena y seleccione el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador").

![Abrir un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "visualizador de cadenas abierto")

## <a name="view-string-visualizer-data"></a>Ver datos de cadena visualizador

En la ventana del visualizador de cadenas, la **expresión** campo muestra la variable o expresión que está encima, y el **valor** campo muestra el valor de cadena. 

Un espacio en blanco **valor** significa que el visualizador elegido no reconoce la cadena. Por ejemplo, el **Visualizador XML** muestra un espacio en blanco **valor** para una cadena de texto sin etiquetas XML o una cadena JSON. 

Para ver las cadenas que no se reconoce el visualizador elegido, elija el **visualizador de texto**. El **visualizador de texto** muestra texto sin formato.

### <a name="view-json-string-data"></a>Ver datos de cadena JSON

Una cadena JSON con formato correcto es similar a la siguiente ilustración, en el visualizador JSON. JSON con formato incorrecto puede mostrar un icono de error (o en blanco si no reconocido). Para identificar el error JSON, copie y pegue la cadena en una herramienta de detección de errores JSON como [JSLint](https://www.jslint.com/).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "visualizador de cadenas JSON")

### <a name="view-xml-string-data"></a>Ver datos de cadena XML

Una cadena XML con formato correcto es similar a la siguiente ilustración, en el visualizador de XML. XML con formato incorrecto puede mostrar sin las etiquetas XML, o en blanco si no se reconoce.

![Visualizador de cadenas XML](../debugger/media/dbg-string-visualizers-xml.png "visualizador de cadenas XML")

### <a name="view-html-string-data"></a>Datos de cadena de la vista HTML

Una cadena HTML que tiene el formato correcto aparece como si se representa en un explorador, como se muestra en la siguiente ilustración. HTML con formato incorrecto puede aparecer como texto sin formato.

![Visualizador de cadenas HTML](../debugger/media/dbg-string-visualizers-html.png "visualizador de cadenas de HTML")

## <a name="see-also"></a>Vea también  
 [Crear visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
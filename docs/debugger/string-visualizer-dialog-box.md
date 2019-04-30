---
title: Cuadro de diálogo del visualizador de cadena | Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 982db296fd17fb86b4a139e02a9418eeb507cd91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902546"
---
# <a name="string-visualizer-dialog-box"></a>Visualizador de cadenas (cuadro de diálogo)

Durante la depuración en Visual Studio, puede ver las cadenas con el visualizador de cadenas integrada. El visualizador de cadenas muestra las cadenas que son demasiado grandes para una ventana de sugerencia o depurador de datos. También puede ayudarle a identificar cadenas con formato incorrecto.

El visualizador de cadenas integrada incluye texto sin formato, XML, HTML y JSON opciones. También puede abrir los visualizadores integrados para algunos otros tipos, tales como [DataSet, DataTable y DataView](../debugger/dataset-visualizer-dialog-box.md) objetos, desde el **automático** u otras ventanas del depurador.

> [!NOTE]
> Si necesita inspeccionar elementos XAML o UI de WPF en un visualizador, vea o [propiedades XAML inspeccionar durante la depuración](../debugger/inspect-xaml-properties-while-debugging.md) o [cómo usar el visualizador de árboles WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Para abrir el visualizador de cadenas, debe ponerse en pausa durante la depuración. Mantenga el mouse sobre una variable que tiene un texto sin formato, XML, HTML o JSON el valor de cadena y seleccione el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador").

## <a name="uielement-list"></a>Lista de UIElement

**Expresión** campo muestra la variable o expresión que está encima.

**Valor** campo muestra el valor de cadena. Un espacio en blanco **valor** significa que el visualizador elegido no reconoce la cadena. Por ejemplo, el **Visualizador XML** muestra un espacio en blanco **valor** para una cadena de texto sin etiquetas XML o una cadena JSON. Para ver las cadenas que no se reconoce el visualizador elegido, elija el **visualizador de texto** en su lugar. El **visualizador de texto** muestra texto sin formato.

### <a name="json-string-data"></a>Datos de cadena JSON

Una cadena JSON con formato correcto es similar a la siguiente ilustración, en el visualizador JSON. JSON con formato incorrecto puede mostrar un icono de error (o en blanco si no reconocido). Para identificar el error JSON, copie y pegue la cadena en una herramienta de detección de errores JSON como [JSLint](https://www.jslint.com/).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "visualizador de cadenas JSON")

### <a name="xml-string-data"></a>Datos de cadena XML

Una cadena XML con formato correcto es similar a la siguiente ilustración, en el visualizador de XML. XML con formato incorrecto puede mostrar sin las etiquetas XML, o en blanco si no se reconoce.

![Visualizador de cadenas XML](../debugger/media/dbg-string-visualizers-xml.png "visualizador de cadenas XML")

### <a name="html-string-data"></a>Datos de cadena HTML

Una cadena HTML que tiene el formato correcto aparece como si se representa en un explorador, como se muestra en la siguiente ilustración. HTML con formato incorrecto puede aparecer como texto sin formato.

![Visualizador de cadenas HTML](../debugger/media/dbg-string-visualizers-html.png "visualizador de cadenas de HTML")

## <a name="see-also"></a>Vea también

- [Crear visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizaciones de datos en Visual Studio para Mac](/visualstudio/mac/data-visualizations)
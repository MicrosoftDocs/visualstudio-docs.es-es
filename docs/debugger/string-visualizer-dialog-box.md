---
title: Cuadro de diálogo visualizador de cadenas | Microsoft Docs
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
ms.openlocfilehash: 10e7e50ffc0cb61bd036bef65c554e8147eecc09
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430820"
---
# <a name="string-visualizer-dialog-box"></a>Visualizador de cadenas (cuadro de diálogo)

Durante la depuración en Visual Studio, puede ver las cadenas con el visualizador de cadenas integrado. El visualizador de cadenas muestra cadenas demasiado largas para una sugerencia de datos o una ventana del depurador. También puede ayudarle a identificar cadenas con un formato incorrecto.

El visualizador de cadenas integrado incluye opciones de texto sin formato, XML, HTML y JSON. También puede abrir visualizadores integrados para unos cuantos otros tipos, como objetos [DataSet, DataTable y DataView](../debugger/dataset-visualizer-dialog-box.md) , desde las ventanas **automático** u otras ventanas del depurador.

> [!NOTE]
> Si necesita inspeccionar los elementos de la interfaz de usuario de WPF o XAML en un visualizador, vea o [inspeccionar las propiedades XAML durante la depuración](../xaml-tools/inspect-xaml-properties-while-debugging.md) o [usar el visualizador de árboles de WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Para abrir el visualizador de cadenas, debe estar en pausa durante la depuración. Mantenga el mouse sobre una variable que tenga un valor de texto sin formato, XML, HTML o cadena JSON y seleccione el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador").

## <a name="uielement-list"></a>Lista de UIElement

Campo de **expresión** muestra la variable o expresión por la que está desplazando el puntero sobre ella.

Campo de **valor** muestra el valor de cadena. Un **valor** en blanco significa que el visualizador elegido no puede reconocer la cadena. Por ejemplo, el **visualizador XML** muestra un **valor** en blanco para una cadena de texto sin etiquetas XML o una cadena JSON. Para ver las cadenas que el visualizador elegido no puede reconocer, elija el **visualizador de texto** en su lugar. El **visualizador de texto** muestra el texto sin formato.

### <a name="json-string-data"></a>Datos de cadena JSON

Una cadena JSON con el formato correcto es similar a la siguiente ilustración del visualizador JSON. Los JSON con formato incorrecto pueden mostrar un icono de error (o en blanco si no se reconocen). Para identificar el error JSON, copie y pegue la cadena en una herramienta de detección de errores de JSON como [JSLint](https://www.jslint.com/).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizador de cadenas JSON")

### <a name="xml-string-data"></a>Datos de cadena XML

Una cadena XML con el formato correcto es similar a la siguiente ilustración del visualizador XML. El XML con formato incorrecto puede mostrarse sin las etiquetas XML o estar en blanco si no se reconoce.

![Visualizador de cadena XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizador de cadena XML")

### <a name="html-string-data"></a>Datos de cadena HTML

Una cadena HTML con el formato correcto aparece como si se representara en un explorador, como se muestra en la siguiente ilustración. El HTML con formato incorrecto puede mostrarse como texto sin formato.

![Visualizador de cadenas HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizador de cadenas HTML")

## <a name="see-also"></a>Vea también

- [Crear visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizaciones de datos en Visual Studio para Mac](/visualstudio/mac/data-visualizations)
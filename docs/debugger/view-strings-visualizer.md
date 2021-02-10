---
title: Ver cadenas en un visualizador de cadenas | Microsoft Docs
description: Use el visualizador de cadenas en el depurador de Visual Studio para ver cadenas de texto, así como cadenas en formato XML, HTML y JSON. Puede ver otros tipos de objetos, incluidos DataSet y DataTable.
ms.custom: SEO-VS-2020
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 287b5e4546d720160c5e73d19cfeaee5bc0c59e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933068"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Ver cadenas en un visualizador de cadenas en Visual Studio

Durante la depuración en Visual Studio, puede ver las cadenas con el visualizador de cadenas integrado. En el visualizador de cadenas se muestran cadenas demasiado largas para una sugerencia de datos o una ventana del depurador. También puede ayudarle a identificar cadenas con un formato incorrecto.

El visualizador de cadenas integrado incluye opciones de texto sin formato, XML, HTML y JSON. También puede abrir visualizadores integrados para otros tipos, como los objetos [DataSet, DataTable y DataView](../debugger/dataset-visualizer-dialog-box.md), desde la ventana **Automático** u otras del depurador.

> [!NOTE]
> Si tiene que inspeccionar elementos de interfaz de usuario de WPF o XAML en un visualizador, vea [Inspección de las propiedades XAML durante la depuración](../xaml-tools/inspect-xaml-properties-while-debugging.md) o [Procedimiento para usar el visualizador de árboles de WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Apertura de un visualizador de cadenas

Para abrir el visualizador de cadenas, la depuración debe estar en pausa. Mantenga el mouse sobre una variable que tenga un valor de cadena de texto sin formato, XML, HTML o JSON, y seleccione el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador").

![Apertura de un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "Abrir el visualizador de cadenas")

## <a name="view-string-visualizer-data"></a>Ver los datos del visualizador de cadenas

En la ventana del visualizador de cadenas, en el campo **Expresión** se muestra la variable o expresión sobre las que se mantiene el puntero, y el campo **Valor** muestra el valor de cadena.

Un **valor** en blanco significa que el visualizador elegido no puede reconocer la cadena. Por ejemplo, el **Visualizador XML** muestra un **valor** en blanco para una cadena de texto sin etiquetas XML, o una cadena JSON.

Para ver las cadenas que el visualizador seleccionado no puede reconocer, elija el **Visualizador de texto**. En el **Visualizador de texto** se muestra el texto sin formato.

### <a name="view-json-string-data"></a>Ver los datos de cadenas JSON

Una cadena JSON con el formato correcto es similar a la ilustración siguiente en el visualizador de JSON. El código JSON con formato incorrecto puede mostrar un icono de error (o en blanco si no se reconoce). Para identificar el error de JSON, copie y pegue la cadena en una herramienta de linting de JSON como [JSLint](https://www.jslint.com/).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizador de cadenas JSON")

### <a name="view-xml-string-data"></a>Ver datos de cadenas XML

Una cadena XML con el formato correcto es similar a la ilustración siguiente en el visualizador de XML. El XML con formato incorrecto puede mostrarse sin las etiquetas XML o estar en blanco si no se reconoce.

![Visualizador de cadenas XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizador de cadenas XML")

### <a name="view-html-string-data"></a>Ver datos de cadenas HTML

Una cadena HTML con el formato correcto aparece como si se representara en un explorador, como se muestra en la ilustración siguiente. El HTML con formato incorrecto se puede mostrar como texto sin formato.

![Visualizador de cadenas HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizador de cadenas HTML")

## <a name="see-also"></a>Vea también

- [Creación de visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizaciones de datos en Visual Studio para Mac](/visualstudio/mac/data-visualizations)
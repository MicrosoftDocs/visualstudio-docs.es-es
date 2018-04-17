---
title: Ver cadenas en un visualizador de cadenas | Documentos de Microsoft
ms.custom: ''
ms.date: 07/11/2017
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 637e046ff99bfaee01ec2484c784d69734ff5118
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Ver las cadenas en un visualizador de cadenas en Visual Studio
Durante la depuración, puede abrir un visualizador de cadenas para ver las cadenas que son demasiado largos para ver en una ventana de punta o el depurador de datos. En muchos escenarios, el visualizador puede ayudarle a identificar las cadenas con formato incorrecto.

Los visualizadores estándar cadena integrada incluyen texto sin formato, XML, HTML y JSON. Para ver algunos otros tipos, como los objetos WPF que aparecen en el depurador de windows como el **automático** ventana, también puede abrir los visualizadores.

## <a name="open-a-string-visualizer"></a>Abrir un visualizador de cadenas

Para ver un texto sin formato, la cadena XML, HTML o JSON, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador") manteniendo el mouse sobre una variable que contiene un valor de cadena. Debe ponerse en pausa en el depurador para ver el icono de lupa.

![Abrir un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Ver datos de cadena

El **expresión** campo en el visualizador de cadenas muestra la actual variable o expresión que se mantiene el mouse sobre en el depurador.

El **valor** campo muestra el valor de cadena. El visualizador de texto muestra el texto sin formato.

Un espacio en blanco **valor** indica que el visualizador específico no reconoce el tipo de cadena. Por ejemplo, el Visualizador XML muestra un espacio en blanco **valor** para la cadena de formato de una cadena de texto simple (con sin etiquetas XML) o JSON. Si necesita ver una cadena irreconocible en un visualizador, usar el visualizador de texto.

### <a name="view-json-string-data"></a>Ver datos de cadena JSON

Una cadena JSON con formato correcto se parecerá a la siguiente ilustración en el visualizador JSON. JSON con formato incorrecto puede mostrar un icono de error (o en blanco si no se reconoce).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "visualizador de cadenas JSON")

### <a name="view-xml-string-data"></a>Ver datos de cadena XML

Una cadena XML con formato correcto se parecerá a la siguiente ilustración en el Visualizador XML. XML con formato incorrecto puede mostrar sin las etiquetas XML (o en blanco si no se reconoce).

![Visualizador de cadenas XML](../debugger/media/dbg-string-visualizers-xml.png "visualizador de cadenas XML")

### <a name="view-html-string-data"></a>Datos de cadena de la vista HTML

Una cadena HTML con formato correcto es similar a la vista que vería si la cadena se representa en un explorador, como se muestra en la siguiente ilustración. HTML con formato incorrecto puede mostrar como texto sin formato.

![Visualizador de cadenas HTML](../debugger/media/dbg-string-visualizers-html.png "visualizador de cadenas de HTML")

## <a name="see-also"></a>Vea también  
 [Crear los visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
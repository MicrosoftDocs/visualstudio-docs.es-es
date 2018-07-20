---
title: Ver cadenas en un visualizador de cadenas | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
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
ms.openlocfilehash: ca6e4519a85659b36e5cf6baebaadd1d1c626f1a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151040"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Ver cadenas en un visualizador de cadenas en Visual Studio
Durante la depuración, puede abrir un visualizador de cadenas para ver las cadenas que son demasiado grande para verla en una ventana de sugerencia o depurador de datos. En muchos escenarios, el visualizador puede ayudarle a identificar cadenas con formato incorrecto.

Los visualizadores estándar cadena integrada incluyen texto sin formato, XML, HTML y JSON. Para ver algunos otros tipos como objetos WPF que aparecen en el depurador de windows como el **automático** ventana, también puede abrir los visualizadores.

## <a name="open-a-string-visualizer"></a>Abrir un visualizador de cadenas

Para ver un texto sin formato, una cadena JSON, HTML o XML, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador") al mantener el mouse sobre una variable que contiene un valor de cadena. Debe ponerse en pausa en el depurador para ver el icono de lupa.

![Abrir un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Ver datos de cadena

El **expresión** campo en el visualizador de cadenas muestra la variable actual o la expresión al mantener el mouse sobre en el depurador.

El **valor** campo muestra el valor de cadena. El visualizador de texto muestra el texto sin formato.

Un espacio en blanco **valor** indica que el visualizador específico no reconoce el tipo de cadena. Por ejemplo, el visualizador de XML muestra un espacio en blanco **valor** para una simple cadena de texto (sin etiquetas XML) o un archivo JSON de cadena con formato. Si tiene que ver una cadena no reconocible en un visualizador, use el visualizador de texto.

### <a name="view-json-string-data"></a>Ver datos de cadena JSON

Una cadena JSON con formato correcto se parecerá a la siguiente ilustración, en el visualizador JSON. JSON con formato incorrecto puede mostrar un icono de error (o en blanco si no reconocido). Si ve un icono de error, copie y pegue la cadena JSON en una herramienta de detección de errores JSON como [JSLint](https://www.jslint.com/) para identificar el error JSON.

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "visualizador de cadenas JSON")

### <a name="view-xml-string-data"></a>Ver datos de cadena XML

Una cadena XML con formato correcto se parecerá a la siguiente ilustración, en el visualizador de XML. XML con formato incorrecto puede mostrar sin las etiquetas XML (o en blanco si no reconocido).

![Visualizador de cadenas XML](../debugger/media/dbg-string-visualizers-xml.png "visualizador de cadenas XML")

### <a name="view-html-string-data"></a>Datos de cadena de la vista HTML

Una cadena HTML que tiene el formato correcto es similar a la vista que vería si la cadena se representa en un explorador, como se muestra en la siguiente ilustración. HTML con formato incorrecto puede aparecer como texto sin formato.

![Visualizador de cadenas HTML](../debugger/media/dbg-string-visualizers-html.png "visualizador de cadenas de HTML")

## <a name="see-also"></a>Vea también  
 [Crear visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
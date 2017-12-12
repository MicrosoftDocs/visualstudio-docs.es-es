---
title: Comportamiento del editor | Microsoft Docs
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 3515dfbf3a7cf8c23178aa9df243638f955593e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="editor-behavior"></a>Comportamiento del editor

Puede establecer los comportamientos del editor de modo que permitan aplicar formato al código mientras se escribe. Estas acciones se establecen en **Visual Studio > Preferencias… > Editor de texto > Comportamiento**. Más abajo se describen algunas de las funciones más usadas:

![Opciones de comportamiento del editor](media/source-editor-image9.png)

*  Se pueden agregar llaves de cierre automáticamente al código al crear clases, métodos o propiedades. Cuando se selecciona esta opción, al escribir `{` se agregará `}` automáticamente.
* La aplicación de formato de código sobre la marcha se activa al pulsar caracteres (por ejemplo, el punto y coma o las llaves), lo que emulará las preferencias de formato establecidas.
* También puede optar por aplicar formato al archivo al guardarlo, lo que permite escribir el código libremente y hace que el IDE sea el responsable de aplicarle formato según las preferencias existentes.
* La sangría se puede establecer en Ninguna, Automática o Inteligente. Hacen lo siguiente:
 * Ninguna: establece el símbolo de inserción al principio de la línea siguiente.
 * Automática: establece el símbolo de inserción en la misma columna de la línea siguiente.
 * Inteligente: aplica la sangría en la línea siguiente en función del código.
* El comportamiento de separación de palabras difiere entre los sistemas operativos y, con vistas a la navegación, el editor de texto debe saber dónde empiezan y acaban las palabras. El formato se puede establecer en Unix o Windows.

También puede establecer reglas de formato para XML, CSS, HTML y JSON.
---
title: "Fragmentos de código con Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 55d7e61f1066de900d6568a848a0aa78e3fd3897
ms.contentlocale: es-es
ms.lasthandoff: 07/12/2017

---

# <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código en Visual Studio proporcionan accesos directos para insertar rápidamente bloques de código de cualquier longitud, lo que evita que tenga que escribir código similar una y otra vez. Herramientas de R para Visual Studio (RTVS) agrega docenas de fragmentos de código de R útiles a la colección de Visual Studio.

Para insertar un fragmento de código, escriba el nombre abreviado del fragmento de código (se proporciona IntelliSense) y después presione Tab para insertar.

Algunos ejemplos sencillos:

- escriba `=` y después presione Tab y RTVS lo expande al operador de asignación `<-`.
- escriba `>` y después presione Tab y RTVS lo expande al operador de canalización `%>%`.

Los fragmentos de código pueden ser mucho más que una simple finalización de caracteres. Un fragmento de código para leer un archivo CSV con la función `read.csv`, por ejemplo, puede evitar tener que recordar los nombres o los parámetros:

![Animación del uso de un fragmento de código para insertar una llamada a read.csv](media/code-snippet-expansion.gif)

En este caso, a medida que escribe `readc`, IntelliSense muestra una lista de finalización. Si selecciona esa finalización en la lista desplegable y presiona Tab, se selecciona `readc` y, si vuelve a presionar Tab, se expande el fragmento de código. (Por esta razón, la expansión de fragmentos de código se suele considerar como "escriba el fragmento de código y presione la tecla Tab dos veces"). En la mayoría de los casos, la primera vez que se presiona Tab, se completa la selección de IntelliSense y, la segunda vez que se presiona Tab, se desencadena la expansión.

Para ver todos los fragmentos de código disponibles, abra el cuadro de diálogo **Herramientas > Administrador de fragmentos de código...** (Ctrl+K,B) y seleccione **R** en **Lenguaje**. Expanda los grupos y seleccione fragmentos de código individuales para ver una descripción y el texto del acceso directo:

![Cuadro de diálogo Fragmentos de código de R](media/code-snippet-dialog.png)

Para crear fragmentos de código personalizados, siga las instrucciones en [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md). Por último, un fragmento de código es solo un archivo XML. Por ejemplo, el siguiente código es el fragmento de código de la operación de canalización (acceso directo `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Los archivos XML de todos los fragmentos de código se instalan con RTVS; el campo **Ubicación** en el **Administrador de fragmentos de código** proporciona la ruta de acceso. También los puede encontrar en el código fuente de RTVS en GitHub en [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).


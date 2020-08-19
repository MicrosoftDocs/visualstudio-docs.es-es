---
title: Fragmentos de código para R
description: Los fragmentos de código para R en Visual Studio ofrecen accesos directos para insertar rápidamente bloques de código de cualquier longitud, lo que evita que tenga que escribir código similar una y otra vez.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 31dfa975cea519d4d064856090a265b844f265f6
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238730"
---
# <a name="code-snippets-for-r"></a>Fragmentos de código para R

Los fragmentos de código en Visual Studio proporcionan accesos directos para insertar rápidamente bloques de código de cualquier longitud, lo que evita que tenga que escribir código similar una y otra vez. Herramientas de R para Visual Studio (RTVS) agrega docenas de fragmentos de código de R útiles a la colección de Visual Studio.

Para insertar un fragmento de código, escriba el nombre abreviado del fragmento de código (se proporciona IntelliSense) y después presione **Tab** para insertar.

Algunos ejemplos sencillos:

- escriba `=` y después presione Tab y RTVS lo expande al operador de asignación `<-`.
- escriba `>` y después presione Tab y RTVS lo expande al operador de canalización `%>%`.

Los fragmentos de código pueden ser mucho más que una simple finalización de caracteres. Un fragmento de código para leer un archivo CSV con la función `read.csv`, por ejemplo, puede evitar tener que recordar los nombres o los parámetros:

![Animación del uso de un fragmento de código para insertar una llamada a read.csv](media/code-snippet-expansion.gif)

En este caso, a medida que escribe `readc`, IntelliSense muestra una lista de finalización. Si selecciona esa finalización en la lista desplegable y presiona **Tab**, se selecciona `readc` y, si vuelve a presionar **Tab**, se expande el fragmento de código. (Por esta razón, la expansión de fragmentos de código se suele considerar como "escriba el fragmento de código y presione la tecla Tab dos veces"). En la mayoría de los casos, la primera vez que se presiona Tab, se completa la selección de IntelliSense y, la segunda vez que se presiona Tab, se desencadena la expansión.

Para ver todos los fragmentos de código disponibles, abra el cuadro de diálogo **Herramientas** > **Administrador de fragmentos de código** (**Ctrl**+**K**,**B**) y seleccione **R** en **Idioma**. Expanda los grupos y seleccione fragmentos de código individuales para ver una descripción y el texto del acceso directo:

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

---
title: "Fragmentos de código con Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código en Visual Studio proporcionan accesos directos para insertar rápidamente bloques de código de cualquier longitud, lo que evita que tenga que escribir código similar una y otra vez. Herramientas de R para Visual Studio (RTVS) agrega docenas de fragmentos de código de R útiles a la colección de Visual Studio.

Para insertar un fragmento de código, escriba el nombre abreviado del fragmento de código (se proporciona IntelliSense) y después presione Tab para insertar.

Algunos ejemplos sencillos:

- escriba `=` y después presione Tab y RTVS lo expande al operador de asignación `<-`.
- escriba `>` y después presione Tab y RTVS lo expande al operador de canalización `%>%`.

Los fragmentos de código pueden ser mucho más que una simple finalización de caracteres. Por ejemplo, puede evitarle tener que recordar los nombres de parámetros en una llamada de función compleja, por ejemplo, este fragmento de código para leer un archivo CSV con la función `read.csv`:

![Animación del uso de un fragmento de código para insertar una llamada a read.csv](media/code-snippet-expansion.gif)

En este caso, a medida que escribe `readc`, IntelliSense muestra una lista de finalización. Si selecciona esa finalización en la lista desplegable y presiona Tab, se selecciona `readc` y, si vuelve a presionar Tab, se expande el fragmento de código. (Por esta razón, la expansión de fragmentos de código se suele considerar como "escriba el fragmento de código y presione la tecla Tab dos veces"). En la mayoría de los casos, la primera vez que se presiona Tab, se completa la selección de IntelliSense y, la segunda vez que se presiona Tab, se desencadena la expansión.

Para ver todos los fragmentos de código disponibles, abra el cuadro de diálogo **Herramientas > Administrador de fragmentos de código...** (Ctrl+K,B) y seleccione **R** en **Lenguaje**. Expanda los grupos y seleccione fragmentos de código individuales para ver una descripción y el texto del acceso directo:

![Cuadro de diálogo Fragmentos de código de R](media/code-snippet-dialog.png)

Para crear fragmentos de código personalizados, siga las instrucciones en [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md). Por último, un fragmento de código es solo un archivo XML. Por ejemplo, el siguiente es el fragmento de código de la operación de canalización (acceso directo `>`)

Tenga en cuenta que un fragmento de código es solo un archivo XML; este es el fragmento de código del operador de canalización:

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


---
title: 'Tutorial: Depurar una hoja de estilos XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e04a2baa31c9fbcd7dd9c2ceeba7ed0840e8b28
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930082"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Tutorial: Depurar una hoja de estilos XSLT

En este tutorial se indican los pasos para utilizar el depurador de XSLT. Éstos incluyen ver variables, definir puntos de interrupción y examinar el código. La hoja de estilos busca todos los libros cuyo costo sea menor que el costo promedio.

## <a name="to-prepare-for-this-walkthrough"></a>Pasos preliminares de este tutorial

1.  Cierre las soluciones que estén abiertas.

2.  Copie los dos archivos de ejemplo en el equipo local.

## <a name="start-debugging"></a>Iniciar depuración

### <a name="to-start-debugging"></a>Para iniciar la depuración

1.  Desde el **archivo** menú, elija **abierto**y haga clic en **archivo**.

2.  Busque el *belowAvg.xsl* de archivo y haga clic en **abierto**.

     La hoja de estilos se abre en el Editor XML.

3.  Haga clic en el botón Examinar (**...** ) en el **entrada** campo de la ventana de propiedades de documento.

4.  Busque el *books.xml* de archivo y haga clic en **abierto**.

     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.

5.  Haga clic en el `xsl:if` etiqueta de inicio, seleccione **punto de interrupción**y haga clic en **Insertar punto de interrupción**.

6.  Haga clic en el **Depurar XSL** en la barra de herramientas del Editor XML.

Comienza el proceso de depuración y se abren varias ventanas nuevas que utiliza el depurador.

Existen dos ventanas que muestran el documento de entrada y la hoja de estilos. El depurador usa estas ventanas para mostrar el estado de ejecución actual. El depurador se posiciona en el `xsl:if` elemento de la hoja de estilos y en el primer nodo de libro en el *books.xml* archivo.

El **variables locales** ventana muestra todas las variables locales y sus valores actuales. Aquí se incluyen las variables definidas en la hoja de estilos así como las que utiliza el depurador para realizar el seguimiento de los nodos que en ese momento existen en contexto.

El **resultado XSL** ventana muestra el resultado de la transformación XSL. Esta ventana es distinta de la **salida de Visual Studio** ventana.

## <a name="watch-window"></a>Ventana Inspección

### <a name="to-use-the-watch-window"></a>Para utilizar la ventana Inspección

1.  Desde el **depurar** menú, elija **Windows**, apunte a **inspección**y haga clic en **Inspección 1**.

     Esto hace que el **Inspección 1** ventana visible.

2.  Tipo `$bookAverage` en el **nombre** campo y presione **ENTRAR**.

     El valor de la variable `$bookAverage` se muestra en la ventana.

3.  Tipo `self::node()` en el **nombre** campo y presione **ENTRAR**.

     `self::node()` es una expresión XPath que se evalúa para el nodo de contexto actual. El valor de la expresión XPath `self::node()` es el primer nodo de libro. Esto cambia a medida que progresamos en la transformación.

4.  Expanda el nodo `self::node()` y, a continuación expanda el nodo `price`.

     De esta manera verá el valor del precio del libro y podrá compararlo fácilmente con el valor `$bookAverage`. Como el precio del libro está por debajo de la media, se debe cumplir la condición `xsl:if`.

## <a name="step-through-the-code"></a>Recorrer el código
 El depurador permite ejecutar código de línea en línea.

### <a name="to-step-through-the-code"></a>Para examinar el código

1.  Presione **F5** para continuar.

     Dado que el primer nodo de libro satisface la `xsl:if` condición, el nodo de libro se agrega a la **resultado XSL** ventana. El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador se ha situado en el segundo nodo de libro en el *books.xml* archivo.

     En el **Inspección 1** ventana el `self::node()` cambia el valor para el segundo nodo de libro. Mediante el examen del valor del elemento de precio, se puede determinar que el precio está por encima de la media, así que la condición `xsl:if` no debería cumplirse.

2.  Presione **F5** para continuar.

     Dado que el segundo nodo de libro no cumple el `xsl:if` condición, el nodo de libro no se agrega a la **resultado XSL** ventana. El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador está colocado en la tercera `book` nodo en el *books.xml* archivo.

     En el **Inspección 1** ventana el `self::node()` cambia el valor al tercer nodo de libro. Mediante el examen del valor del elemento `price`, se puede determinar que el precio está por debajo de la media, así que debería cumplirse la condición `xsl:if`.

3.  Presione **F5** para continuar.

     Dado que el `xsl:if` se cumplió la condición, el tercer libro se agrega a la **resultado XSL** ventana. Todos los libros del documento XML se han procesado y el depurador se detiene.

## <a name="sample-files"></a>Archivos de ejemplo

El tutorial utiliza los dos siguientes archivos de ejemplo.

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Vea también

- [Depuración de XSLT](../xml-tools/debugging-xslt.md)
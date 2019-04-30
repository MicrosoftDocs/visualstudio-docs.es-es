---
title: Depurar hojas de estilos XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808517"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Tutorial: Depuración de una hoja de estilos XSLT

En este tutorial se indican los pasos para utilizar el depurador de XSLT. Éstos incluyen ver variables, definir puntos de interrupción y examinar el código. El depurador permite ejecutar código de línea a la vez.

Para prepararse para este tutorial, primero copie los dos [archivos de ejemplo](#sample-files) en el equipo local. Una es la hoja de estilos, y uno es el archivo XML que vamos a usar como entrada para la hoja de estilos. En este tutorial, usamos la hoja de estilos busca todos los libros cuyo costo está por debajo del precio medio de los libros.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="start-debugging"></a>Iniciar depuración

1. Desde el **archivo** menú, elija **abierto** > **archivo**.

2. Busque el *debajo average.xsl* de archivo y elija **abierto**.

   Se abre la hoja de estilos en el editor XML.

3. Haga clic en el botón Examinar (**...** ) en el **entrada** campo de la ventana de propiedades de documento. (Si la **propiedades** ventana no está visible, haga doble clic en cualquier lugar en el archivo abierto en el editor y, a continuación, elija **propiedades**.)

4. Busque el *books.xml* de archivo y, a continuación, elija **abierto**.

   Esto establece el archivo de documento de origen que se usa para la transformación XSLT.

5. Establecer un [punto de interrupción](../debugger/using-breakpoints.md) en 12 de la línea *debajo average.xsl*. Puede hacerlo de varias maneras:

   - Haga clic en el margen del editor en la línea 12.

   - Haga clic en cualquier lugar en la línea 12 y, a continuación, presione **F9**.

   - Haga clic en el `xsl:if` etiqueta de apertura y, a continuación, elija **punto de interrupción** > **Insertar punto de interrupción**.

      ![Insertar punto de interrupción en el archivo XSL en Visual Studio](media/insert-breakpoint.PNG)

6. En la barra de menús, elija **XML** > **iniciar la depuración de XSLT** (o presione **Alt**+**F5**).

   Se inicia el proceso de depuración.

   En el editor, el depurador se posiciona en el `xsl:if` elemento de la hoja de estilos. Otro archivo denominado *debajo average.xml* se abre en el editor; este es el archivo de salida que se rellenará como cada nodo en el archivo de entrada *books.xml* se procesa.

   El **automático**, **variables locales**, y **Inspección 1** ventanas aparecen en la parte inferior de la ventana de Visual Studio. El **variables locales** ventana muestra todas las variables locales y sus valores actuales. Aquí se incluyen las variables definidas en la hoja de estilos así como las que utiliza el depurador para realizar el seguimiento de los nodos que en ese momento existen en contexto.

## <a name="watch-window"></a>Ventana Inspección

Vamos a agregar dos variables para el **Inspección 1** ventana, por lo que podemos examinar sus valores cuando se procesa el archivo de entrada. (También puede usar el **variables locales** ventana para examinar los valores si las variables que va a inspeccionar ya están ahí.)

1. Desde el **depurar** menú, elija **Windows** > **inspección** > **Inspección 1**.

   El **Inspección 1** ventana se vuelve visible.

2. Tipo `$bookAverage` en el **nombre** campo y, a continuación, presione **ENTRAR**.

   El valor de la `$bookAverage` variable que se muestra en el **valor** campo.

3. En la línea siguiente, escriba `self::node()` en el **nombre** campo y, a continuación, presione **ENTRAR**.

   `self::node()` es una expresión XPath que se evalúa para el nodo de contexto actual. El valor de la expresión XPath `self::node()` es el primer nodo de libro. Esto cambia a medida que progresamos en la transformación.

4. Expanda el `self::node()` nodo y, a continuación, expanda el nodo que tiene es el valor `price`.

   ![Ventana Inspección durante la depuración de XSLT en Visual Studio](media/xslt-debugging-watch-window.png)

   Puede ver el valor del precio del libro para el nodo de libro actual y compararlo con el `$bookAverage` valor. Dado que el precio del libro está por debajo del promedio, el `xsl:if` condición debe ser exitosa al continuar el proceso de depuración.

## <a name="step-through-the-code"></a>Recorrer el código

1. Presione **F5** para continuar.

   Dado que el primer nodo de libro satisface la `xsl:if` condición, el nodo de libro se agrega a la *debajo average.xml* archivo de salida. El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador se ha situado en el segundo nodo de libro en el *books.xml* archivo.

   En el **Inspección 1** ventana, el `self::node()` cambia el valor para el segundo nodo de libro. Mediante el examen del valor del elemento de precio, se puede determinar que el precio está por encima de la media, así que la condición `xsl:if` no debería cumplirse.

2. Presione **F5** para continuar.

   Porque el segundo nodo de libro no cumple el `xsl:if` condición, el nodo de libro no se agrega a la *debajo average.xml* archivo de salida. El depurador continúa ejecutándose hasta que se coloca de nuevo en el `xsl:if` elemento en la hoja de estilos. El depurador está colocado en la tercera `book` nodo en el *books.xml* archivo.

   En el **Inspección 1** ventana, el `self::node()` cambia el valor al tercer nodo de libro. Examinando el valor de la `price` elemento, puede determinar que el precio está por debajo del promedio. El `xsl:if` condición debe ejecutarse correctamente.

3. Presione **F5** para continuar.

   Dado que el `xsl:if` se cumplió la condición, el tercer libro se agrega a la *debajo average.xml* archivo de salida. Todos los libros del documento XML se han procesado y el depurador se detiene.

## <a name="sample-files"></a>Archivos de ejemplo

El tutorial utiliza los dos siguientes archivos de ejemplo.

### <a name="below-averagexsl"></a>below-average.xsl

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
        <xsl:if test="price &lt; $bookAverage">
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
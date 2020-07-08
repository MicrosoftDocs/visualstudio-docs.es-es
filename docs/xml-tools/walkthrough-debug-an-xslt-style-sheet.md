---
title: Depuración de hojas de estilos XSLT
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c75d3cae07101363f6c986a1defb375f602f466
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815128"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Tutorial: Depuración de una hoja de estilos XSLT

En este tutorial se indican los pasos para utilizar el depurador de XSLT. Éstos incluyen ver variables, definir puntos de interrupción y examinar el código. El depurador permite ejecutar código de línea en línea.

Para prepararse para este tutorial, copie primero los dos [archivos de ejemplo](#sample-files) en el equipo local. Uno es la hoja de estilos y otro es el archivo XML que se utilizará como entrada para la hoja de estilos. En este tutorial, la hoja de estilos que usamos busca todos los libros cuyo costo sea inferior al precio medio de los libros.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="start-debugging"></a>Iniciar depuración

1. En el menú **Archivo**, elija **Abrir** > **Archivo**.

2. Busque el archivo *below-average.xsl* y elija **Abrir**.

   La hoja de estilos se abre en el Editor XML.

3. Haga clic en el botón Examinar ( **...** ) en el campo **Entrada** de la ventana de propiedades del documento. (Si la ventana **Propiedades** no está visible, haga clic con el botón secundario en cualquier parte del archivo abierto en el editor y, a continuación, elija **Propiedades**).

4. Busque el archivo *books.xml* y, a continuación, elija **Abrir**.

   De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.

5. Establezca un [punto de interrupción](../debugger/using-breakpoints.md) en la línea 12 de *below-average.xsl*. Puede hacerlo de una de varias maneras:

   - Haga clic en el margen del editor en la línea 12.

   - Haga clic en cualquier parte de la línea 12 y, a continuación, presione **F9**.

   - Haga clic con el botón derecho en la etiqueta de inicio de `xsl:if` y, a continuación, elija **Punto de interrupción** > **Insertar punto de interrupción**.

      ![Insertar punto de interrupción en un archivo XSL en Visual Studio](media/insert-breakpoint.PNG)

6. En la barra de menús, elija **XML** > **Iniciar depuración de XSLT** (o presione **Alt**+**F5**).

   Se inicia el proceso de depuración.

   En el editor, el depurador se coloca en el elemento `xsl:if` de la hoja de estilos. Otro archivo llamado *below-average.xml* se abre en el editor; este es el archivo de salida que se rellenará a medida que se procese cada nodo del archivo de entrada *books.xml*.

   Las ventanas **Automático**, **Locales** e **Inspección 1** aparecen en la parte inferior de la ventana de Visual Studio. La ventana **Locales** muestra todas las variables locales y sus valores actuales. Aquí se incluyen las variables definidas en la hoja de estilos así como las que utiliza el depurador para realizar el seguimiento de los nodos que en ese momento existen en contexto.

## <a name="watch-window"></a>Ventana Inspección

Vamos a agregar dos variables a la ventana **Inspección 1** para que podamos examinar sus valores a medida que se procesa el archivo de entrada. (También puede usar la ventana **Locales** para examinar valores si las variables que desea inspeccionar ya están allí).

1. En el menú **Depurar**, elija **Ventanas** > **Inspección** > **Inspección 1**.

   La ventana **Inspección 1** se vuelve visible.

2. Escriba `$bookAverage` en el campo **Nombre** y presione **Entrar**.

   El valor de la variable `$bookAverage` se muestra en el campo **Valor**.

3. En la línea siguiente, escriba `self::node()` en el campo **Nombre** y, a continuación, presione **Entrar**.

   `self::node()` es una expresión XPath que se evalúa para el nodo de contexto actual. El valor de la expresión XPath `self::node()` es el primer nodo de libro. Esto cambia a medida que progresamos en la transformación.

4. Expanda el nodo `self::node()` y, a continuación expanda el nodo cuyo valor es `price`.

   ![Ventana Inspección durante la depuración XSLT en Visual Studio](media/xslt-debugging-watch-window.png)

   Puede ver el valor del precio del libro para el nodo de libro actual y compararlo con el valor `$bookAverage`. Como el precio del libro está por debajo de la media, se debe cumplir la condición `xsl:if` al continuar con el proceso de depuración.

## <a name="step-through-the-code"></a>Recorrido del código

1. Presione **F5** para continuar.

   Como el primer nodo de libro satisface la condición `xsl:if`, se agrega el nodo de libro al archivo de salida *below-average.xml*. El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador se coloca en el segundo nodo de libro del archivo *books.xml*.

   En la ventana **Inspección 1**, el valor `self::node()` cambia al segundo nodo de libro. Mediante el examen del valor del elemento de precio, se puede determinar que el precio está por encima de la media, así que la condición `xsl:if` no debería cumplirse.

2. Presione **F5** para continuar.

   Como el segundo nodo de libro no satisface la condición `xsl:if`, no se agrega al archivo de salida *below-average.xml*. El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador está colocado en el tercer nodo de `book` del archivo *books.xml*.

   En la ventana **Inspección 1**, el valor `self::node()` cambia al tercer nodo de libro. Mediante el examen del valor del elemento `price`, se puede determinar que el precio está por debajo de la media. La condición `xsl:if` debe ser correcta.

3. Presione **F5** para continuar.

   Como la condición `xsl:if` se ha cumplido, el tercer libro se agrega al archivo de salida *below-average.xml*. Todos los libros del documento XML se han procesado y el depurador se detiene.

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

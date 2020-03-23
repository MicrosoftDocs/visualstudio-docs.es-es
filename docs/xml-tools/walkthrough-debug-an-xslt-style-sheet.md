---
title: Depurar hojas de estilo XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79300946"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Tutorial: Depurar una hoja de estilos XSLT

En este tutorial se indican los pasos para utilizar el depurador de XSLT. Éstos incluyen ver variables, definir puntos de interrupción y examinar el código. El depurador le permite ejecutar código una línea a la vez.

Para prepararse para este tutorial, copie primero los dos archivos de [ejemplo](#sample-files) en el equipo local. Una es la hoja de estilos, y otra es el archivo XML que usaremos como entrada para la hoja de estilos. En este tutorial, la hoja de estilos que usamos encuentra todos los libros cuyo costo está por debajo del precio medio del libro.

> [!NOTE]
> El depurador XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="start-debugging"></a>Iniciar la depuración

1. En el menú **Archivo,** elija **Abrir** > **archivo**.

2. Busque el *archivo below-average.xsl* y elija **Open**.

   La hoja de estilos se abre en el editor XML.

3. Haga clic en el botón Examinar (**...**) en el campo **Entrada** de la ventana de propiedades del documento. (Si la ventana **Propiedades** no está visible, haga clic con el botón derecho en cualquier parte del archivo abierto en el editor y, a continuación, elija **Propiedades**.)

4. Busque el archivo *books.xml* y, a continuación, elija **Open**.

   Esto establece el archivo de documento de origen que se usa para la transformación XSLT.

5. Establezca un punto de [interrupción](../debugger/using-breakpoints.md) en la línea 12 de *below-average.xsl*. Puede hacerlo de varias maneras:

   - Haga clic en el margen del editor en la línea 12.

   - Haga clic en cualquier lugar de la línea 12 y, a continuación, presione **F9**.

   - Haga clic `xsl:if` con el botón derecho en la etiqueta de inicio y, a continuación, elija **Punto** > de interrupción Insertar punto de**interrupción**.

      ![Insertar punto de interrupción en el archivo XSL en Visual Studio](media/insert-breakpoint.PNG)

6. En la barra de menús, elija **DEPURAción XML** > **Start XSLT** (o, presione **Alt**+**F5**).

   Se inicia el proceso de depuración.

   En el editor, el depurador `xsl:if` se coloca en el elemento de la hoja de estilos. Otro archivo denominado *below-average.xml* se abre en el editor; este es el archivo de salida que se rellenará a medida que se procese cada nodo del archivo de entrada *books.xml.*

   Las **ventanas Autos**, **Locales**y **Inspección 1** aparecen en la parte inferior de la ventana de Visual Studio. La ventana **Locales** muestra todas las variables locales y sus valores actuales. Aquí se incluyen las variables definidas en la hoja de estilos así como las que utiliza el depurador para realizar el seguimiento de los nodos que en ese momento existen en contexto.

## <a name="watch-window"></a>Ventana Inspección

Agregaremos dos variables a la ventana **Inspección 1** para que podamos examinar sus valores a medida que se procesa el archivo de entrada. (También puede utilizar la ventana **Locales** para examinar los valores si las variables que desea ver ya están allí.)

1. En el menú **Depurar** , elija **Windows** > **Watch** > **Watch 1**.

   La ventana **Inspección 1** se hace visible.

2. Escriba `$bookAverage` el campo **Nombre** y, a continuación, presione **ENTRAR**.

   El valor `$bookAverage` de la variable se muestra en el campo **Valor.**

3. En la siguiente `self::node()` línea, escriba el campo **Nombre** y, a continuación, presione **ENTRAR**.

   `self::node()`es una expresión XPath que se evalúa como el nodo de contexto actual. El valor de la expresión XPath `self::node()` es el primer nodo de libro. Esto cambia a medida que progresamos en la transformación.

4. Expanda `self::node()` el nodo y, a continuación, expanda `price`el nodo que el valor es .

   ![Ventana ver durante la depuración XSLT en Visual Studio](media/xslt-debugging-watch-window.png)

   Puede ver el valor del precio contable para el nodo `$bookAverage` contable actual y compararlo con el valor. Dado que el precio del `xsl:if` libro está por debajo del promedio, la condición debe realizarse correctamente al continuar el proceso de depuración.

## <a name="step-through-the-code"></a>Paso a través del código

1. Presione **F5** para continuar.

   Dado que el primer `xsl:if` nodo de libro cumple la condición, el nodo book se agrega al archivo de salida *below-average.xml.* El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador ahora se coloca en el segundo nodo de libro del archivo *books.xml.*

   En la ventana **Inspección 1,** el `self::node()` valor cambia al segundo nodo de libro. Mediante el examen del valor del elemento de precio, se puede determinar que el precio está por encima de la media, así que la condición `xsl:if` no debería cumplirse.

2. Presione **F5** para continuar.

   Dado que el segundo nodo `xsl:if` de libro no cumple la condición, el nodo book no se agrega al archivo de salida *below-average.xml.* El depurador continúa ejecutándose hasta que se `xsl:if` coloca de nuevo en el elemento de la hoja de estilos. El depurador ahora se coloca `book` en el tercer nodo del archivo *books.xml.*

   En la ventana **Inspección 1,** el `self::node()` valor cambia al tercer nodo de libro. Al examinar el valor `price` del elemento, puede determinar que el precio está por debajo del promedio. La `xsl:if` condición debe tener éxito.

3. Presione **F5** para continuar.

   Dado `xsl:if` que se cumplió la condición, el tercer libro se agrega al archivo de salida *below-average.xml.* Todos los libros del documento XML se han procesado y el depurador se detiene.

## <a name="sample-files"></a>Archivos de ejemplo

El tutorial utiliza los dos siguientes archivos de ejemplo.

### <a name="below-averagexsl"></a>por debajo de average.xsl

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

## <a name="see-also"></a>Consulte también

- [Depuración de XSLT](../xml-tools/debugging-xslt.md)

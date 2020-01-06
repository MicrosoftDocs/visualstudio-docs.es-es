---
title: Depurar hojas de estilos XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592482"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Tutorial: depurar una hoja de estilos XSLT

En este tutorial se indican los pasos para utilizar el depurador de XSLT. Éstos incluyen ver variables, definir puntos de interrupción y examinar el código. El depurador permite ejecutar código de línea en línea.

Para prepararse para este tutorial, copie primero los dos [archivos de ejemplo](#sample-files) en el equipo local. Una es la hoja de estilos y otra es el archivo XML que se utilizará como entrada para la hoja de estilos. En este tutorial, la hoja de estilos que usamos busca todos los libros cuyo costo sea inferior al precio medio de los libros.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="start-debugging"></a>Iniciar depuración

1. En el menú **archivo** , elija **abrir** **archivo**de > .

2. Busque el archivo *below-Average. xsl* y elija **abrir**.

   Se abre la hoja de estilos en el editor XML.

3. Haga clic en el botón Examinar ( **...** ) en el campo de **entrada** de la ventana Propiedades del documento. (Si la ventana **propiedades** no está visible, haga clic con el botón secundario en cualquier parte del archivo abierto en el editor y, a continuación, elija **propiedades**).

4. Busque el archivo *books. XML* y, a continuación, elija **abrir**.

   Esto establece el archivo de documento de origen que se usa para la transformación XSLT.

5. Establezca un [punto de interrupción](../debugger/using-breakpoints.md) en la línea 12 de *below-Average. xsl*. Puede hacerlo de una de varias maneras:

   - Haga clic en el margen del editor en la línea 12.

   - Haga clic en cualquier parte de la línea 12 y, a continuación, presione **F9**.

   - Haga clic con el botón derecho en la etiqueta de inicio de `xsl:if` y, a continuación, elija **punto de interrupción** > **Insertar punto de interrupción**.

      ![Insertar punto de interrupción en un archivo XSL en Visual Studio](media/insert-breakpoint.PNG)

6. En la barra de menús, elija **XML** > **iniciar depuración de XSLT** (o presione **Alt**+**F5**).

   Se inicia el proceso de depuración.

   En el editor, el depurador se coloca en el `xsl:if` elemento de la hoja de estilos. Se abre otro archivo llamado *below-Average. XML* en el editor; Este es el archivo de salida que se rellenará cuando se procese cada nodo del archivo de entrada *books. XML* .

   Las ventanas **automático**, **variables locales**e **inspección 1** aparecen en la parte inferior de la ventana de Visual Studio. La ventana **variables locales** muestra todas las variables locales y sus valores actuales. Aquí se incluyen las variables definidas en la hoja de estilos así como las que utiliza el depurador para realizar el seguimiento de los nodos que en ese momento existen en contexto.

## <a name="watch-window"></a>Ventana de inspección

Vamos a agregar dos variables a la ventana **inspección 1** para que podamos examinar sus valores a medida que se procesa el archivo de entrada. (También puede usar la ventana **variables locales** para examinar los valores si las variables que desea inspeccionar ya están allí).

1. En el menú **depurar** , elija **Windows** > **Ver** > **inspección 1**.

   La ventana **inspección 1** se vuelve visible.

2. Escriba `$bookAverage` en el campo **nombre** y, a continuación, presione **entrar**.

   El valor de la variable `$bookAverage` se muestra en el campo **valor** .

3. En la línea siguiente, escriba `self::node()` en el campo **nombre** y, a continuación, presione **entrar**.

   `self::node()` es una expresión XPath que se evalúa como el nodo de contexto actual. El valor de la expresión XPath `self::node()` es el primer nodo de libro. Esto cambia a medida que progresamos en la transformación.

4. Expanda el nodo `self::node()` y, a continuación, expanda el nodo que tiene el valor `price`.

   ![ventana Inspección durante la depuración XSLT en Visual Studio](media/xslt-debugging-watch-window.png)

   Puede ver el valor del precio del libro para el nodo de libro actual y compararlo con el valor de `$bookAverage`. Dado que el precio del libro está por debajo del promedio, la condición `xsl:if` debe realizarse correctamente cuando se continúa el proceso de depuración.

## <a name="step-through-the-code"></a>Recorrer paso a paso el código

1. Presione **F5** para continuar.

   Dado que el primer nodo de libro cumple la condición de `xsl:if`, el nodo de libro se agrega al archivo de salida *below-Average. XML* . El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos. El depurador se encuentra ahora en el segundo nodo de libro del archivo *books. XML* .

   En la ventana **inspección 1** , el valor `self::node()` cambia al segundo nodo de libro. Mediante el examen del valor del elemento de precio, se puede determinar que el precio está por encima de la media, así que la condición `xsl:if` no debería cumplirse.

2. Presione **F5** para continuar.

   Dado que el segundo nodo de libro no cumple la condición de `xsl:if`, el nodo de libro no se agrega al archivo de salida *below-Average. XML* . El depurador continúa ejecutándose hasta que se vuelve a colocar en el elemento `xsl:if` de la hoja de estilos. El depurador ahora está situado en el tercer nodo de `book` en el archivo *books. XML* .

   En la ventana **inspección 1** , el valor `self::node()` cambia al tercer nodo de libro. Al examinar el valor del elemento `price`, puede determinar que el precio está por debajo del promedio. La condición `xsl:if` debe ser correcta.

3. Presione **F5** para continuar.

   Dado que se ha satisfecho la condición de `xsl:if`, el tercer libro se agrega al archivo de salida *below-Average. XML* . Todos los libros del documento XML se han procesado y el depurador se detiene.

## <a name="sample-files"></a>Archivos de muestra

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

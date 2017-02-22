---
title: "Tutorial: Depurar una hoja de estilos XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tutorial: Depurar una hoja de estilos XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se indican los pasos para utilizar el depurador de XSLT.Éstos incluyen ver variables, definir puntos de interrupción y examinar el código.La hoja de estilos busca todos los libros cuyo costo sea menor que el costo promedio.  
  
### Para prepararse para este tutorial  
  
1.  Cierre las soluciones que estén abiertas.  
  
2.  Copie los dos archivos de ejemplo en el equipo local.  
  
## Inicie la depuración  
  
#### Para iniciar la depuración  
  
1.  En el menú **Archivo**, seleccione **Abrir** y haga clic en **Archivo**.  
  
2.  Busque el archivo belowAvg.xsl y haga clic en **Abrir**.  
  
     La hoja de estilos se abre en el Editor XML.  
  
3.  Haga clic en el botón Examinar \(**...**\) en el campo **Entrada** de la ventana Propiedades del documento.  
  
4.  Busque el archivo books.xsl y haga clic en **Abrir**.  
  
     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.  
  
5.  Haga clic con el botón secundario en la etiqueta de apertura `xsl:if`, seleccione **Punto de interrupción** y haga clic en **Insertar punto de interrupción**.  
  
6.  Haga clic en el botón **Depurar XSL** en la barra de herramientas del Editor XML.  
  
 Comienza el proceso de depuración y se abren varias ventanas nuevas que utiliza el depurador.  
  
 Existen dos ventanas que muestran el documento de entrada y la hoja de estilos.El depurador usa estas ventanas para mostrar el estado de ejecución actual.El depurador se posiciona en el elemento `xsl:if` de la hoja de estilos y en el primer nodo de libro del archivo books.xml.  
  
 La ventana Locales muestra todas las variables locales y sus valores actuales.Aquí se incluyen las variables definidas en la hoja de estilos así como las que utiliza el depurador para realizar el seguimiento de los nodos que en ese momento existen en contexto.  
  
 La **Ventana de salida de XSL** muestra el resultado de la transformación XSL.Esta ventana es distinta de la **Ventana de salida de Visual Studio**.  
  
## Ventana Inspección  
  
#### Para utilizar la ventana Inspección  
  
1.  En el menú **Depurar**, seleccione **Ventanas**, **Inspección** y haga clic en **Inspección 1**.  
  
     Se muestra la ventana Inspección 1.  
  
2.  Escriba `$bookAverage` en el campo **Nombre** y presione INTRO.  
  
     El valor de la variable `$bookAverage` se muestra en la ventana.  
  
3.  Escriba `self::node()` en el campo **Nombre** y presione INTRO.  
  
     `self::node()` es una expresión XPath que se evalúa para el nodo de contexto actual.El valor de la expresión XPath `self::node()` es el primer nodo de libro.Esto cambia a medida que progresamos en la transformación.  
  
4.  Expanda el nodo `self::node()` y, a continuación expanda el nodo `price`.  
  
     De esta manera verá el valor del precio del libro y podrá compararlo fácilmente con el valor `$bookAverage`.Como el precio del libro está por debajo de la media, se debe cumplir la condición `xsl:if`.  
  
## Examinar el código  
 El depurador permite ejecutar código de línea en línea.  
  
#### Para examinar el código  
  
1.  Presione **F5** para continuar.  
  
     Como el primer nodo de libro satisface la condición `xsl:if`, se agrega a la ventana de salida de XSL.El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos.El depurador se coloca en el segundo nodo de libro del archivo books.xml.  
  
     En la ventana Watch1, el valor `self::node()` cambia al segundo nodo de libro.Mediante el examen del valor del elemento de precio, se puede determinar que el precio está por encima de la media, así que la condición `xsl:if` no debería cumplirse.  
  
2.  Presione **F5** para continuar.  
  
     Como el segundo nodo de libro no satisface la condición `xsl:if`, no se agrega a la ventana de salida de XSL.El depurador continúa ejecutándose hasta que se coloca de nuevo en el elemento `xsl:if` de la hoja de estilos.El depurador está colocado en el tercer nodo de `book` del archivo books.xml.  
  
     En la ventana Watch1, el valor `self::node()` cambia al tercer nodo de libro.Mediante el examen del valor del elemento `price`, se puede determinar que el precio está por debajo de la media, así que debería cumplirse la condición `xsl:if`.  
  
3.  Presione **F5** para continuar.  
  
     Como la condición `xsl:if` se ha cumplido, el tercer libro se agrega a la ventana de salida de XSL.Todos los libros del documento XML se han procesado y el depurador se detiene.  
  
## Archivos de ejemplo  
 El tutorial utiliza los dos siguientes archivos de ejemplo.  
  
### belowAvg.xsl  
  
```  
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
  
### books.xml  
  
```  
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
  
## Vea también  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)
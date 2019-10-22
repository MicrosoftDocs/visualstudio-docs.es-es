---
title: 'Tutorial: uso de la jerarquía de XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46e6acc8f65a9c9589348508f57cc75b04c61ccc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669559"
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Tutorial: Usar la herramienta Jerarquía XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta Jerarquía XSLT simplifica muchas tareas de desarrollo de XML. Una hoja de estilos XSLT usa a menudo instrucciones `includes` e `imports`. La compilación se inicia desde la hoja de estilos principal, pero cuando aparece un error como resultado de compilar una hoja de estilos XSLT, dicho error puede proceder de un origen distinto de la hoja de estilos principal. Es posible que se requiera acceso a las hojas de estilos importadas o incluidas para corregir el error o editar la hoja de estilos. Es posible que la ejecución paso a paso de la hoja de estilos en el depurador le permita abrir las hojas de estilos importadas e incluidas, y si lo desea puede agregar un punto de interrupción en algún punto en una o varias de las hojas de estilos incluidas.

 Otro escenario en el que la herramienta Jerarquía XSLT puede ser de utilidad es la colocación de puntos de interrupción en las reglas de plantilla integradas. Las reglas de plantilla son plantillas especiales generadas para cada modo de la hoja de estilos y a las que llama el elemento `xsl:apply-templates` cuando ninguna otra plantilla coincide con el nodo. Para implementar la depuración en las reglas de plantilla integradas, el depurador XSLT genera el archivo con las reglas en la carpeta temporal y las compila junto con la hoja de estilos principal. Si no se ejecuta paso a paso el código desde algún elemento `xsl:apply-template`, puede resultar complicado encontrar las hojas de estilos incluidas en la hoja de estilos principal o localizar y abrir la hoja de estilos con las reglas de plantilla integradas.

 El ejemplo de este tema muestra la depuración en una hoja de estilos a la que se hace referencia.

### <a name="procedure-title"></a>Título del procedimiento

1. Abra un documento XML en Visual Studio. Este ejemplo usa el documento `collection.xml` siguiente.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

2. Agregue el archivo `xslincludefile.xsl` siguiente:

    ```
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3. Agregue el archivo `xslinclude.xsl` siguiente:

    ```
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4. Agregue un punto de interrupción en la instrucción: `<xsl:include href="xslincludefile.xsl" />`

5. Inicie la depuración.

6. Cuando el depurador se detenga en la instrucción `<xsl:include href="xslincludefile.xsl" />`, presione el botón Paso a paso por instrucciones. Observe que la depuración puede continuar en la hoja de estilos a la que se hace referencia. La jerarquía está visible y el diseñador muestra la ruta de acceso correcta.

## <a name="see-also"></a>Vea también
 [Tutorial: Generador de perfiles XSLT](../xml-tools/walkthrough-xslt-profiler.md)

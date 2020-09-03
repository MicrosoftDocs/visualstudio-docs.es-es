---
title: 'Tutorial: usar IntelliSense para XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b65f2279270be0d5baef16d6d06e35a7fb0b854
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669541"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Tutorial: Uso de XSLT IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial muestra cómo usar XSLT de IntelliSense para autocompletar los valores de algunos atributos.

### <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Para usar IntelliSense en el atributo de nombre de elementos xsl:with-param y xsl:call-template

1. Cree un nuevo archivo XSLT y copie en él el código siguiente:

    ```
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. Coloque el cursor después de `<xsl:template name="msg23" match="msg23">` y presione ENTRAR. A continuación, comience a escribir el elemento `xsl:call-template` siguiente:

    ```
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     La lista de nombres de plantilla aparece en el atributo `name=""` del elemento `xsl:call-template` a medida que se escribe.

3. Coloque el cursor después de `<xsl:call-template name="localized-message">` y presione ENTRAR. A continuación, comience a escribir el elemento `xsl:with-param` siguiente:

    ```
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     La lista de nombres de parámetro aparece en el atributo `name=""` del elemento `xsl:with-param`.

### <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Para usar IntelliSense en el atributo de modo de un elemento xsl:apply-templates

1. Cree un nuevo archivo XSLT y copie en él el código siguiente:

    ```
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Coloque el cursor después de `<xsl:apply-templates select="phone" />` y presione ENTRAR. A continuación, comience a escribir el elemento `xsl: apply-templates` siguiente:

    ```
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     La lista de modos de plantilla aparece en el atributo `mode=""` del elemento `xsl:apply-templates`.

### <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Para usar IntelliSense en los atributos stylesheet-prefix y result-prefix de un elemento xsl:namespace-alias

1. Cree un nuevo archivo XSLT y copie en él el código siguiente:

    ```
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Coloque el cursor después de `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` y presione ENTRAR. A continuación, comience a escribir el elemento `xsl:namespace-alias` siguiente:

    ```
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Observe cómo la lista de prefijos ha aparecido en los atributos `stylesheet-prefix` y `result-prefix` del elemento `xsl:namespace-alias`.

## <a name="see-also"></a>Consulte también
 [Características de IntelliSense del editor XML](../xml-tools/xml-editor-intellisense-features.md)

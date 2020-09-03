---
title: 'Tutorial: Uso de XSLT IntelliSense'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a085627d598bfcc969c2e76d717a2f49a31922b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817286"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Tutorial: Uso de XSLT IntelliSense

Este tutorial muestra cómo usar XSLT de IntelliSense para autocompletar los valores de algunos atributos.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Para usar IntelliSense en el atributo de nombre de elementos xsl:with-param y xsl:call-template

1. Cree un nuevo archivo XSLT y copie en él el código siguiente:

    ```xml
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

2. Coloque el cursor después de `<xsl:template name="msg23" match="msg23">` y presione **ENTRAR**. A continuación, comience a escribir el elemento `xsl:call-template` siguiente:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     La lista de nombres de plantilla aparece en el atributo `name=""` del elemento `xsl:call-template` a medida que se escribe.

3. Coloque el cursor después de `<xsl:call-template name="localized-message">` y presione **ENTRAR**. A continuación, comience a escribir el elemento `xsl:with-param` siguiente:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     La lista de nombres de parámetro aparece en el atributo `name=""` del elemento `xsl:with-param`.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Para usar IntelliSense en el atributo de modo de un elemento xsl:apply-templates

1. Cree un nuevo archivo XSLT y copie en él el código siguiente:

    ```xml
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

2. Coloque el cursor después de `<xsl:apply-templates select="phone" />` y presione **ENTRAR**. A continuación, comience a escribir el elemento `xsl: apply-templates` siguiente:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     La lista de modos de plantilla aparece en el atributo `mode=""` del elemento `xsl:apply-templates`.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Para usar IntelliSense en los atributos stylesheet-prefix y result-prefix de un elemento xsl:namespace-alias

1. Cree un nuevo archivo XSLT y copie en él el código siguiente:

    ```xml
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

2. Coloque el cursor después de `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` y presione **ENTRAR**. A continuación, comience a escribir el elemento `xsl:namespace-alias` siguiente:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Observe cómo la lista de prefijos ha aparecido en los atributos `stylesheet-prefix` y `result-prefix` del elemento `xsl:namespace-alias`.

## <a name="see-also"></a>Vea también

- [Características de IntelliSense del Editor XML](../xml-tools/xml-editor-intellisense-features.md)

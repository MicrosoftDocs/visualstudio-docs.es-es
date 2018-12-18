---
title: Características de IntelliSense del Editor XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78a9711a623abe2f7a37cb03be628c2b60723359
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886388"
---
# <a name="xml-editor-intellisense-features"></a>Características de IntelliSense del Editor XML

El Editor XML proporciona completas características IntelliSense comparables a las de otros editores de lenguajes proporcionados en Visual Studio. En esta sección se explica cómo puede usar IntelliSense con el lenguaje de definición de esquemas XML (XSD) y con documentos XSLT.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense en un documento XSD
 Después de un esquema se asocia con el documento, obtendrá una lista desplegable de elementos esperados cada vez que escribe `"<"` o haga clic en el **mostrar una lista de miembros de objeto** botón en la barra de herramientas del editor XML. Para obtener información acerca de cómo asociar esquemas con documentos XML, vea [validación de documentos XML](../xml-tools/xml-document-validation.md).

 Si escribe SPACE desde dentro de una etiqueta de apertura, también obtendrá una lista desplegable con todos los atributos que se pueden agregar al elemento actual.

 Si escribe `"="` en un valor de atributo, o las comillas de apertura del valor, también obtendrá la lista de valores posibles para ese atributo. Los valores solo se proporcionan si el esquema incluye valores enumerados mediante facetas `xsd:enumeration`, o si el atributo es del tipo `Boolean`. También se proporciona una lista IntelliSense de códigos de lenguajes conocidos para `xml:lang` o para cualquier `simpleType` que se obtenga de `xsd:language`. Se proporciona una lista IntelliSense de valores `targetNamespace` conocidos para las declaraciones de espacio de nombres.

 También se proporciona una lista IntelliSense de valores posibles si escribe `">"` para cerrar una etiqueta de apertura cuando el elemento es un `simpleType`. El comportamiento de los elementos es similar al de los atributos descritos en el párrafo anterior.

 También aparece en estas listas IntelliSense información sobre herramientas en función de la información de `xsd:annotation` y `xsd:documentation` encontrada en el esquema asociado.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense en un documento XSLT
 Después de agregar una plantilla con nombre o un atributo a un documento XSLT, puede usar IntelliSense para insertar lo siguiente:

-   Nombres de conjuntos de atributos.

-   Modos de plantilla.

-   Nombres de plantilla.

-   Nombres de parámetro para un modo determinado.

-   Nombres de parámetro para una plantilla con nombre determinada.

Para obtener más información, consulte [Tutorial: usar XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) tema.

## <a name="auto-completion"></a>Finalización automática
 El Editor XML también facilita la edición de XML al rellenar automáticamente la sintaxis XML necesaria. Por ejemplo, si escribe la siguiente etiqueta de apertura:

 `<book>`

 El Editor XML rellena la etiqueta de cierre y coloca el cursor después de la etiqueta de apertura. El siguiente es un ejemplo de esto (la "&#124;" notas de la posición del cursor):

 `<book>`&#124;`</book>`

 Como los valores de atributo deben ir siempre entre comillas, el Editor XML rellena las comillas automáticamente. Por ejemplo, si escribe:

 `<book title=`

 El Editor XML agrega las comillas y coloca el cursor entre ellas:

 `<book title="`&#124;`"`

 De igual forma, el Editor XML también inserta la siguiente sintaxis XML de forma automática:

-   Finalizar una instrucción de procesamiento: `?>`

-   Finalizar un bloque CDATA: `]]>`

-   Finalizar un comentario: `-->`

-   Finalizar una declaración DTD: `>`

El editor XML también tiene la capacidad para insertar un espacio de nombres si selecciona un espacio de nombres completo del elemento o atributo de una lista de IntelliSense y el espacio de nombres de ese elemento o atributo no está aún en el ámbito de declaración.

Por ejemplo, si selecciona el elemento `e:Book` de la lista IntelliSense en la que el prefijo está enlazado con el espacio de nombres `http://books` que no se ha declarado en el documento, el Editor XML inserta automáticamente la declaración de espacio de nombres necesaria. A continuación se muestra el texto XML resultante:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Coincidencia de llaves
 El Editor XML proporciona resalte de llaves que le permite obtener información inmediata acerca de los elementos que acaba de cerrar. También puede usar el método abreviado de teclado (**Ctrl**+**]**) para saltar de una llave a la llave correspondiente.

 El Editor XML realiza esta acción en los siguientes elementos:

-   Etiquetas de apertura y cierre coincidentes.

-   Cualquier par de "\<" o ">" entre corchetes angulares.

-   Inicio y fin de comentarios.

-   Inicio y fin de instrucciones de procesamiento.

-   Inicio y fin de bloques CDATA.

-   Inicio y fin de declaraciones DTD.

-   Comillas de apertura y cierre en atributos.

## <a name="modify-the-intellisense-options"></a>Modificar las opciones de IntelliSense
 Las características IntelliSense y finalización automática están habilitadas de forma predeterminada. Sin embargo, puede cambiar esto modificando su **herramientas** > **opciones** configuración.

 El **inserción automática** sección de la **varios** página controla el comportamiento siguiente:

|nombre|Descripción|
|-|-----------------|
|Etiquetas de cierre|Inserta etiquetas de cierre en nuevos elementos.|
|Comillas de atributos|Inserta comillas de valor de atributo cuando se escribe un nuevo nombre de atributo.|
|Otro marcado|Completa comentarios, CDATA, DOCTYPE, instrucciones de procesamiento y otras declaraciones de marcado.|

### <a name="to-change-the-auto-completion-behavior"></a>Para cambiar el comportamiento de finalización automática

1.  Seleccione **Opciones** en el menú **Herramientas**.

2.  Expanda **Editor de texto**, expanda **XML**y seleccione **varios**.

3.  Realice cambios en el **autoinsertar** sección y haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Usar IntelliSense](../ide/using-intellisense.md)
- [Tutorial: Usar XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)
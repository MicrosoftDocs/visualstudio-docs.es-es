---
title: Características de IntelliSense del Editor XML
description: Obtenga información sobre las características de IntelliSense del editor XML de Visual Studio y cómo usarlas con documentos XSLT y de lenguaje de definición de esquema XML (XSD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 330dbdfb6d6db8d33a2b8ea3caa7e1a840d84dd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874904"
---
# <a name="xml-editor-intellisense-features"></a>Características de IntelliSense del editor XML

El Editor XML proporciona completas características IntelliSense comparables a las de otros editores de lenguajes proporcionados en Visual Studio. En esta sección se explica cómo puede usar IntelliSense con el lenguaje de definición de esquemas XML (XSD) y con documentos XSLT.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense en un documento XSD

Una vez que se asocia un esquema con un documento, se obtiene una lista desplegable de elementos esperados cada vez que se escribe `"<"` o se hace clic en el botón **Mostrar un objeto Lista de miembros** en la barra de herramientas del Editor XML.

![Botón Mostrar un objeto Lista de miembros](media/display-object-member-list-xml.png)

Para información sobre cómo asociar esquemas con documentos XML, consulte [Validación de documentos XML](../xml-tools/xml-document-validation.md).

Si escribe SPACE desde dentro de una etiqueta de apertura, también obtendrá una lista desplegable con todos los atributos que se pueden agregar al elemento actual.

Si escribe `"="` en un valor de atributo, o las comillas de apertura del valor, también obtendrá la lista de valores posibles para ese atributo. Los valores solo se proporcionan si el esquema incluye valores enumerados mediante facetas `xsd:enumeration`, o si el atributo es del tipo `Boolean`. También se proporciona una lista IntelliSense de códigos de lenguajes conocidos para `xml:lang` o para cualquier `simpleType` que se obtenga de `xsd:language`. Se proporciona una lista IntelliSense de valores `targetNamespace` conocidos para las declaraciones de espacio de nombres.

También se proporciona una lista IntelliSense de valores posibles si escribe `">"` para cerrar una etiqueta de apertura cuando el elemento es un `simpleType`. El comportamiento de los elementos es similar al de los atributos descritos en el párrafo anterior.

También aparece en estas listas IntelliSense información sobre herramientas en función de la información de `xsd:annotation` y `xsd:documentation` encontrada en el esquema asociado.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense en un documento XSLT

Después de agregar una plantilla con nombre o un atributo a un documento XSLT, puede usar IntelliSense para insertar lo siguiente:

- Nombres de conjuntos de atributos.

- Modos de plantilla.

- Nombres de plantilla.

- Nombres de parámetro para un modo determinado.

- Nombres de parámetro para una plantilla con nombre determinada.

Para obtener más información, vea [Tutorial: Uso de XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md).

## <a name="auto-completion"></a>Finalización automática

El Editor XML también facilita la edición de XML al rellenar automáticamente la sintaxis XML necesaria. Por ejemplo, si escribe la siguiente etiqueta de apertura:

`<book>`

El Editor XML rellena la etiqueta de cierre y coloca el cursor después de la etiqueta de apertura. A continuación se muestra un ejemplo de esto (la barra "|" indica la posición del cursor):

`<book>`&#124;`</book>`

Como los valores de atributo deben ir siempre entre comillas, el Editor XML rellena las comillas automáticamente. Por ejemplo, si escribe:

`<book title=`

El Editor XML agrega las comillas y coloca el cursor entre ellas:

`<book title="`&#124;`"`

De igual forma, el Editor XML también inserta la siguiente sintaxis XML de forma automática:

- Finalizar una instrucción de procesamiento: `?>`

- Finalizar un bloque CDATA: `]]>`

- Finalizar un comentario: `-->`

- Finalizar una declaración DTD: `>`

El Editor XML también tiene la capacidad para insertar una declaración de espacio de nombres si selecciona un elemento o un atributo certificado de espacio de nombres de una lista IntelliSense y el espacio de nombres de ese elemento o atributo no se encuentra aún en el ámbito.

Por ejemplo, si selecciona el elemento `e:Book` de la lista IntelliSense en la que el prefijo está enlazado con el espacio de nombres `http://books` que no se ha declarado en el documento, el Editor XML inserta automáticamente la declaración de espacio de nombres necesaria. A continuación se muestra el texto XML resultante:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Coincidencia de llaves

El Editor XML proporciona resalte de llaves que le permite obtener información inmediata acerca de los elementos que acaba de cerrar. También puede usar el método abreviado de teclado (**Ctrl**+ **]** ) para saltar de una llave a la llave siguiente coincidente.

El Editor XML realiza esta acción en los siguientes elementos:

- Etiquetas de inicio y de cierre coincidentes.

- Cualquier par de corchetes angulares "\<" or ">".

- Inicio y fin de comentarios.

- Inicio y fin de instrucciones de procesamiento.

- Inicio y fin de bloques CDATA.

- Inicio y fin de declaraciones DTD.

- Comillas de apertura y cierre en atributos.

## <a name="modify-the-intellisense-options"></a>Modificación de las opciones de IntelliSense

Las características IntelliSense y finalización automática están habilitadas de forma predeterminada. Sin embargo, puede cambiar esto si modifica la configuración **Herramientas** > **Opciones**.

La sección **Inserción automática** de la página **Varios** controla el comportamiento siguiente:

|NOMBRE|Descripción|
|-|-----------------|
|Etiquetas de cierre|Inserta etiquetas de cierre en nuevos elementos.|
|Comillas de atributos|Inserta comillas de valor de atributo cuando se escribe un nuevo nombre de atributo.|
|Otro marcado|Completa comentarios, CDATA, DOCTYPE, instrucciones de procesamiento y otras declaraciones de marcado.|

### <a name="to-change-the-auto-completion-behavior"></a>Para cambiar el comportamiento de finalización automática

1. Seleccione **Opciones** en el menú **Herramientas**.

2. Expanda **Editor de texto**, **XML** y seleccione **Varios**.

3. Realice los cambios oportunos en la sección **Inserción automática** y haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Usar IntelliSense](../ide/using-intellisense.md)
- [Tutorial: Uso de XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)

---
title: Cuadro de diálogo Esquemas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1f8f4824d18618b40ad4073dc6be0c81d9aba37
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835213"
---
# <a name="xml-schemas-dialog-box"></a>Cuadro de diálogo esquemas XML

El **esquemas XML** cuadro de diálogo se usa para seleccionar qué esquemas XML esquema definición XSD (lenguaje) van a asociar a un documento XML. Podrá seleccionar un esquema de la caché de esquema o especificar un esquema que no está ubicado en la caché. Los esquemas seleccionados se consideran parte de un conjunto de esquemas. IntelliSense y la validación de documentos XML usan el conjunto de esquemas.

Puede tener acceso a la **esquemas XML** cuadro de diálogo haciendo clic en el **esquemas** botón en la ventana Propiedades del documento, o bien seleccionando **esquemas** desde el **XML** menú.

## <a name="uielement-list"></a>Lista de UIElement
 **Use**

 Seleccione cómo usar el esquema XML.

-   **Automática**. Aunque este esquema no se utiliza en el documento actual, está disponible para la asociación automática. Si el documento XML declara un espacio de nombres que coincide con el `targetNamespace` de este esquema, el esquema se asociará automáticamente y se incluirá en el conjunto de esquemas.

-   **Utilizar este esquema**. El documento actual está utilizando este esquema. El usuario ha hecho clic en la columna para usar explícitamente este esquema, o el esquema estaba asociado automáticamente a una coincidencia con `targetNamespace`.

-   **No utilizar esquemas seleccionados**. El documento actual no utiliza este esquema, aunque haya una coincidencia del esquema con `targetNamespace`. Esta configuración puede ser útil para resolver conflictos cuando hay más de una versión del mismo esquema en la solución o caché de esquema.

**Target Namespace**

Muestra el espacio de nombres de destino asociado con el esquema XML.

**Nombre de archivo**

Muestra el nombre de archivo del esquema XML.

**Add**

Se abre el **Abrir esquema XSD** cuadro de diálogo que le permite seleccionar otros esquemas y agregarlos al conjunto de esquemas. Cuando agrega un esquema para el esquema establecido, el **Use** el valor de columna se establece en **utilizar este esquema**.

**Remove**

Quita el esquema seleccionado actualmente del conjunto de esquemas. Esto supone quitar el esquema de la caché de esquema en memoria, pero no del sistema de archivos.

## <a name="see-also"></a>Vea también

- [Componentes del Editor XML](../xml-tools/xml-editor-components.md)
- [Cómo: Seleccione los esquemas XML para usar](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Caché de esquema](../xml-tools/schema-cache.md)
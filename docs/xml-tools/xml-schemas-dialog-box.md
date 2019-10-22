---
title: esquemas XML
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11743756ffd8f59520448d2687dbada6d4eaca40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608047"
---
# <a name="xml-schemas-dialog-box"></a>Cuadro de diálogo Esquemas XML

El cuadro de diálogo **esquemas XML** se utiliza para seleccionar los esquemas del lenguaje de definición de esquemas XML (XSD) que se van a asociar a un documento XML. Podrá seleccionar un esquema de la caché de esquema o especificar un esquema que no está ubicado en la caché. Los esquemas seleccionados se consideran parte de un conjunto de esquemas. IntelliSense y la validación de documentos XML usan el conjunto de esquemas.

Para tener acceso al cuadro de diálogo **esquemas XML** , haga clic en el botón **esquemas** de la ventana Propiedades del documento o seleccione **esquemas** en el menú **XML** .

## <a name="uielement-list"></a>Lista de UIElement

**Realice**

Seleccione cómo usar el esquema XML.

- **Automática**. Aunque este esquema no se utiliza en el documento actual, está disponible para la asociación automática. Si el documento XML declara un espacio de nombres que coincide con el `targetNamespace` de este esquema, el esquema se asociará automáticamente y se incluirá en el conjunto de esquemas.

- **Use este esquema**. El documento actual está utilizando este esquema. El usuario ha hecho clic en la columna para usar explícitamente este esquema, o el esquema estaba asociado automáticamente a una coincidencia con `targetNamespace`.

- **No usar esquemas seleccionados**. El documento actual no utiliza este esquema, aunque haya una coincidencia del esquema con `targetNamespace`. Esta configuración puede ser útil para resolver conflictos cuando hay más de una versión del mismo esquema en la solución o caché de esquema.

**Espacio de nombres de destino**

Muestra el espacio de nombres de destino asociado con el esquema XML.

**Nombre de archivo**

Muestra el nombre de archivo del esquema XML.

**Add**

Abre el cuadro de diálogo **abrir esquema XSD** , que le permite seleccionar esquemas adicionales para agregarlos al conjunto de esquemas. Cuando se agrega un esquema al conjunto de esquemas, el valor **usar** columna se establece para **utilizar este esquema**.

**Remove**

Quita el esquema seleccionado actualmente del conjunto de esquemas. Esto supone quitar el esquema de la caché de esquema en memoria, pero no del sistema de archivos.

## <a name="see-also"></a>Vea también

- [Cómo: seleccionar los esquemas XML que se van a usar](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Caché de esquema](../xml-tools/schema-cache.md)
---
title: esquemas XML
description: Obtenga información sobre el cuadro de diálogo Esquemas XML, que se usa para seleccionar los esquemas del lenguaje de definición de esquema XML (XSD) que se van a asociar a un documento XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26703b821d2748612f461a35591a831488807dbb
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351406"
---
# <a name="xml-schemas-dialog-box"></a>Cuadro de diálogo Esquemas XML

El cuadro de diálogo **Esquemas XML** se usa para seleccionar los esquemas del lenguaje de definición de esquemas XML (XSD) que se van a asociar con un documento XML. Podrá seleccionar un esquema de la caché de esquema o especificar un esquema que no está ubicado en la caché. Los esquemas seleccionados se consideran parte de un conjunto de esquemas. IntelliSense y la validación de documentos XML usan el conjunto de esquemas.

Para tener acceso al cuadro de diálogo **Esquemas XML**, haga clic en el botón **Esquemas** de la ventana Propiedades del documento o seleccione **Esquemas** en el menú **XML**.

## <a name="uielement-list"></a>Lista de UIElement

**Uso**

Seleccione cómo usar el esquema XML.

- **Automática**. Aunque este esquema no se utiliza en el documento actual, está disponible para la asociación automática. Si el documento XML declara un espacio de nombres que coincide con el `targetNamespace` de este esquema, el esquema se asociará automáticamente y se incluirá en el conjunto de esquemas.

- **Utilizar este esquema**. El documento actual está utilizando este esquema. El usuario ha hecho clic en la columna para usar explícitamente este esquema, o el esquema estaba asociado automáticamente a una coincidencia con `targetNamespace`.

- **No utilizar esquemas seleccionados**. El documento actual no utiliza este esquema, aunque haya una coincidencia del esquema con `targetNamespace`. Esta configuración puede ser útil para resolver conflictos cuando hay más de una versión del mismo esquema en la solución o caché de esquema.

**Espacio de nombres de destino**

Muestra el espacio de nombres de destino asociado con el esquema XML.

**Nombre de archivo**

Muestra el nombre de archivo del esquema XML.

**Add**

Abre el cuadro de diálogo **Abrir esquema XSD**, que permite seleccionar otros esquemas y agregarlos al conjunto de esquemas. Al agregar un esquema al conjunto de esquemas, el valor de la columna **Usar** se establece en **Utilizar este esquema**.

**Remove**

Quita el esquema seleccionado actualmente del conjunto de esquemas. Esto supone quitar el esquema de la caché de esquema en memoria, pero no del sistema de archivos.

## <a name="see-also"></a>Vea también

- [Cómo: Selección de los esquemas XML que se van a usar](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Caché de esquemas](../xml-tools/schema-cache.md)

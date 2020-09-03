---
title: Cuadro de diálogo esquemas XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d637cb3c25772685d5a782eb74bf94878ded36c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669421"
---
# <a name="xml-schemas-dialog-box"></a>Cuadro de diálogo Esquemas XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El cuadro de diálogo **Esquemas XML** se usa para seleccionar los esquemas del lenguaje de definición de esquemas XML (XSD) que se van a asociar con un documento XML. Podrá seleccionar un esquema de la caché de esquema o especificar un esquema que no está ubicado en la caché. Los esquemas seleccionados se consideran parte de un conjunto de esquemas. IntelliSense y la validación de documentos XML usan el conjunto de esquemas.

 Para tener acceso al cuadro de diálogo **Esquemas XML**, haga clic en el botón **Esquemas** de la ventana Propiedades del documento o seleccione **Esquemas** en el menú **XML**.

## <a name="uielement-list"></a>Lista de UIElement
 **Usar** Seleccione cómo se va a usar el esquema XML.

- **Automática**. Aunque este esquema no se utiliza en el documento actual, está disponible para la asociación automática. Si el documento XML declara un espacio de nombres que coincide con el `targetNamespace` de este esquema, el esquema se asociará automáticamente y se incluirá en el conjunto de esquemas.

- **Utilizar este esquema**. El documento actual está utilizando este esquema. El usuario ha hecho clic en la columna para usar explícitamente este esquema, o el esquema estaba asociado automáticamente a una coincidencia con `targetNamespace`.

- **No utilizar esquemas seleccionados**. El documento actual no utiliza este esquema, aunque haya una coincidencia del esquema con `targetNamespace`. Esta configuración puede ser útil para resolver conflictos cuando hay más de una versión del mismo esquema en la solución o caché de esquema.

  **Espacio de nombres de destino** Muestra el espacio de nombres de destino asociado con el esquema XML.

  **Nombre de archivo** Muestra el nombre del archivo de esquema XML.

  **Agregar** Abre el cuadro de diálogo **abrir esquema XSD** , que le permite seleccionar esquemas adicionales para agregarlos al conjunto de esquemas. Al agregar un esquema al conjunto de esquemas, el valor de la columna **Usar** se establece en **Utilizar este esquema**.

  **Quitar** Quita el esquema seleccionado actualmente del conjunto de esquemas. Esto supone quitar el esquema de la caché de esquema en memoria, pero no del sistema de archivos.

## <a name="see-also"></a>Consulte también
 [Componentes del editor XML](../xml-tools/xml-editor-components.md) [Cómo: seleccionar los esquemas XML para usar la caché de](../xml-tools/how-to-select-the-xml-schemas-to-use.md) [esquema](../xml-tools/schema-cache.md)

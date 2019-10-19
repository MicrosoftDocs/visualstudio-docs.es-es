---
title: Cómo usar fragmentos de código XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 163fcddb8553da39b035e649155e04c3da4b430e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601795"
---
# <a name="how-to-use-xml-snippets"></a>Cómo: usar fragmentos de código XML

Puede invocar fragmentos XML mediante los dos comandos siguientes en el menú contextual del editor XML. El comando **Insertar fragmento** inserta el fragmento de código XML en la posición del cursor. El comando **rodear con** ajusta el fragmento de código XML alrededor del texto seleccionado. Cada fragmento XML tiene designados tipos de fragmentos. Los tipos de fragmentos de código determinan si el fragmento de código está disponible con el comando **Insertar fragmento** , el comando **rodear con** o ambos.

Una vez que el fragmento XML se ha agregado al editor, todos los campos editables del fragmento se resaltan en amarillo y el cursor se coloca en el primer campo editable.

## <a name="insert-snippet"></a>Insertar fragmento

En los procedimientos siguientes se describe cómo obtener acceso al comando **Insertar fragmento de código** .

> [!NOTE]
> El comando **Insertar fragmento de código** también está disponible a través del método abreviado de teclado (**Ctrl** +**K**y, a continuación, **Ctrl** +**X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Para insertar fragmentos desde el menú contextual

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Haga clic con el botón derecho y seleccione **Insertar fragmento de código**.

   Se muestra una lista de fragmentos XML disponibles.

3. Seleccione un fragmento de código de la lista con el mouse o escriba el nombre del fragmento de código y presione **Tab** o **entrar**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Para insertar fragmentos con el menú IntelliSense

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. En el menú **edición** , seleccione **IntelliSense**y, a continuación, seleccione **Insertar fragmento de código**.

   Se muestra una lista de fragmentos XML disponibles.

3. Seleccione un fragmento de la lista con el mouse o escriba el nombre del fragmento de código y presione **Tab** o **entrar**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Para insertar fragmentos de código a través de la lista de palabras completas de IntelliSense

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Comience a escribir el fragmento XML que desea agregar al archivo. Si la finalización automática está activada, se muestra la lista de palabras completas de IntelliSense. Si no aparece, presione **Ctrl** +**espacio** para activarlo.

3. Seleccione el fragmento XML de la lista de palabras completas.

4. Presione **Tab**para invocar el **fragmento de código** XML.

> [!NOTE]
> Puede haber casos en los que el fragmento XML no se llegue a invocar. Por ejemplo, si intenta insertar un elemento `xs:complexType` dentro de un nodo `xs:element`, el editor no genera un fragmento XML. Cuando un elemento `xs:complexType` se utiliza dentro de un nodo `xs:element`, no están los atributos o subelementos necesarios, así que el editor no tiene datos que insertar.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Para insertar fragmentos con el nombre de acceso directo

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Escriba `<` en el panel del editor.

3. Presione **ESC** para cerrar la lista de palabras completas de IntelliSense.

4. Escriba el nombre de acceso directo del fragmento de código y presione **Tab** para invocar el fragmento de código XML.

## <a name="surround-with"></a>Delimitar con

En los procedimientos siguientes se describe cómo tener acceso al comando **envolver con** .

> [!NOTE]
> El comando **rodear con** también está disponible a través del método abreviado de teclado (**Ctrl** +**K**y, a continuación, **Ctrl** +**S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Para usar el delimitar con en el menú contextual

1. Seleccione el texto que desea envolver en el editor XML.

2. Haga clic con el botón derecho y seleccione **rodear con**.

   Se muestra una lista de bordes disponibles con fragmentos XML.

3. Seleccione un fragmento de código de la lista con el mouse o escriba el nombre del fragmento de código y presione **Tab** o **entrar**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Para usar delimitar con desde el menú de IntelliSense

1. Seleccione el texto que desea envolver en el editor XML.

2. En el menú **edición** , seleccione **IntelliSense**y, a continuación, seleccione **rodear con**.

   Se muestra una lista de bordes disponibles con fragmentos XML.

3. Seleccione un fragmento de código de la lista con el mouse o escriba el nombre del fragmento de código y presione **Tab** o **entrar**.

## <a name="use-xml-snippets"></a>Uso de fragmentos XML

Una vez elegido un fragmento XML, el texto del fragmento de código se inserta automáticamente en la posición del cursor. Todos los campos editables del fragmento se resaltan y el primero de estos campos se selecciona automáticamente. Al campo actualmente seleccionado se le aplica la conversión boxing.

Cuando se selecciona un campo, puede escribir un nuevo valor para el mismo. Al presionar **Tab** , se recorren los campos editables del fragmento de código. al presionar **mayús** +**Tab** se recorren en orden inverso. Al hacer clic en un campo, el cursor se coloca en dicho campo, y al hacer doble clic en él se selecciona. Cuando un campo está resaltado, podría mostrarse información sobre herramientas, que ofrece una descripción del campo.

Solo es editable la primera ocurrencia de un campo dado. Cuando ese campo está resaltado, las demás ocurrencias de dicho campo se destacan. Si cambia el valor de un campo editable, ese campo cambia en cualquier parte en la que se utilice en el fragmento.

Si presiona **entrar** o **ESC** , se cancela la edición de campos y se devuelve el editor a normal.

Los colores predeterminados para los campos de fragmentos de código editables se pueden cambiar modificando el valor del **campo fragmento de código** en el panel **fuentes y colores** del cuadro de diálogo **Opciones** . Para obtener más información, vea [Cómo: cambiar fuentes y colores en el editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Vea también

- [Fragmentos de código XML](../xml-tools/xml-snippets.md)
- [Cómo: generar un fragmento de código XML a partir de un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Cómo: crear fragmentos de código XML](../xml-tools/how-to-create-xml-snippets.md)
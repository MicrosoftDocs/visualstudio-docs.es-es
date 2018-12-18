---
title: Cómo usar los fragmentos XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4758fbebea12b014f92bed59e851210509cdbb9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573133"
---
# <a name="how-to-use-xml-snippets"></a>Cómo: usar XML fragmentos de código

Puede invocar fragmentos XML mediante los dos siguientes comandos del menú contextual del Editor XML. El **Insertar fragmento de código** comando inserta el fragmento XML en la posición del cursor. El **rodear con** comando ajusta el fragmento XML alrededor del texto seleccionado. Cada fragmento XML tiene designados tipos de fragmentos. Los tipos de fragmentos determinan si el fragmento está disponible con la **Insertar fragmento de código** comando, el **rodear con** , o ambos.

Una vez que el fragmento XML se ha agregado al editor, todos los campos editables del fragmento se resaltan en amarillo y el cursor se coloca en el primer campo editable.

## <a name="insert-snippet"></a>Insertar fragmento

Los procedimientos siguientes describen cómo tener acceso a la **Insertar fragmento de código** comando.

> [!NOTE]
> El **Insertar fragmento de código** comando también está disponible mediante el método abreviado de teclado (**Ctrl**+**K**, a continuación, **Ctrl** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Para insertar fragmentos desde el menú contextual

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Haga clic en y seleccione **Insertar fragmento de código**.

   Se muestra una lista de fragmentos XML disponibles.

3. Seleccione un fragmento de la lista con el mouse o escribiendo el nombre del fragmento y presione **ficha** o **ENTRAR**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Para insertar fragmentos con el menú IntelliSense

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Desde el **editar** menú, elija **IntelliSense**y, a continuación, seleccione **Insertar fragmento de código**.

   Se muestra una lista de fragmentos XML disponibles.

3. Seleccione un fragmento de la lista con el mouse o escribiendo el nombre del fragmento y presione **ficha** o **ENTRAR**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Para insertar fragmentos de código a través de la lista de palabras completas de IntelliSense

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Comience a escribir el fragmento XML que desea agregar al archivo. Si la finalización automática está activada, se muestra la lista de palabras completas de IntelliSense. Si no aparece, presione **Ctrl**+**espacio** para activarla.

3. Seleccione el fragmento XML de la lista de palabras completas.

4. Presione **ficha**, **ficha** para invocar el fragmento XML.

> [!NOTE]
> Puede haber casos en los que el fragmento XML no se llegue a invocar. Por ejemplo, si intenta insertar un elemento `xs:complexType` dentro de un nodo `xs:element`, el editor no genera un fragmento XML. Cuando un elemento `xs:complexType` se utiliza dentro de un nodo `xs:element`, no están los atributos o subelementos necesarios, así que el editor no tiene datos que insertar.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Para insertar fragmentos con el nombre de acceso directo

1. Coloque el cursor en el lugar en el que desea insertar el fragmento XML.

2. Escriba `<` en el panel del editor.

3. Presione **Esc** para cerrar la lista de palabras completas de IntelliSense.

4. Escriba el nombre de método abreviado del fragmento y presione **ficha** para invocar el fragmento XML.

## <a name="surround-with"></a>Delimitar con

Los procedimientos siguientes describen cómo tener acceso a la **rodear con** comando.

> [!NOTE]
> El **rodear con** comando también está disponible mediante el método abreviado de teclado (**Ctrl**+**K**, a continuación, **Ctrl** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Usar rodear con en el menú contextual

1. Seleccione el texto que se va a rodear en el Editor XML.

2. Haga clic en y seleccione **rodear con**.

   Se muestra una lista de bordes disponibles con fragmentos XML.

3. Seleccione un fragmento de la lista con el mouse o escribiendo el nombre del fragmento y presione **ficha** o **ENTRAR**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Usar rodear con en el menú de IntelliSense

1. Seleccione el texto que se va a rodear en el Editor XML.

2. Desde el **editar** menú, elija **IntelliSense**y, a continuación, seleccione **rodear con**.

   Se muestra una lista de bordes disponibles con fragmentos XML.

3. Seleccione un fragmento de la lista con el mouse o escribiendo el nombre del fragmento y presione **ficha** o **ENTRAR**.

## <a name="use-xml-snippets"></a>Utilizar fragmentos XML

Una vez elegido un fragmento XML, el texto del fragmento de código se inserta automáticamente en la posición del cursor. Todos los campos editables del fragmento se resaltan y el primero de estos campos se selecciona automáticamente. Al campo actualmente seleccionado se le aplica la conversión boxing.

Cuando se selecciona un campo, puede escribir un nuevo valor para el mismo. Al presionar **ficha** se desplaza por los campos editables del fragmento de código; si presiona **MAYÚS**+**ficha** recorrerá en orden inverso. Al hacer clic en un campo, el cursor se coloca en dicho campo, y al hacer doble clic en él se selecciona. Cuando un campo está resaltado, podría mostrarse información sobre herramientas, que ofrece una descripción del campo.

Solo es editable la primera ocurrencia de un campo dado. Cuando ese campo está resaltado, las demás ocurrencias de dicho campo se destacan. Si cambia el valor de un campo editable, ese campo cambia en cualquier parte en la que se utilice en el fragmento.

Al presionar **ENTRAR** o **Esc** cancela la edición de los campos y el editor vuelve a su estado normal.

Los colores predeterminados de los campos de fragmento de código modificable pueden cambiarse modificando la **campo de fragmento de código** en el **fuentes y colores** panel de la **opciones** cuadro de diálogo. Para obtener más información, consulte [Cómo: cambiar fuentes y colores en el editor de](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Vea también

- [Fragmentos XML](../xml-tools/xml-snippets.md)
- [Cómo: generar un fragmento XML desde un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Cómo: crear fragmentos XML](../xml-tools/how-to-create-xml-snippets.md)
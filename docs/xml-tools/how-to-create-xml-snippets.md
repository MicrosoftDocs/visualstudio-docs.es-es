---
title: Crear fragmentos de código XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df3c2592036f085fcf89d80bcefb1a469b3c1e15
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592755"
---
# <a name="how-to-create-xml-snippets"></a>Cómo: crear fragmentos de código XML

El editor XML se puede utilizar para crear nuevos fragmentos XML. El editor incluye un fragmento XML, llamado "Fragmento", que es un fragmento reutilizable que permite la creación de nuevos fragmentos XML.

## <a name="to-create-a-new-xml-snippet"></a>Para crear un nuevo fragmento XML

Para crear un nuevo fragmento de código XML, cree un nuevo archivo XML y use la característica **Insertar fragmento** de código.

1. En el menú **archivo** , haga clic en **nuevo** y, a continuación, haga clic en **archivo**.

2. Haga clic en **archivo XML** y, a continuación, en **abrir**.

3. Haga clic con el botón derecho en el panel del editor y seleccione **Insertar fragmento de código**.

4. Seleccione **fragmento de código** en la lista y presione **entrar**.

5. Realice los cambios que considere oportunos en el nuevo fragmento.

6. En el menú **archivo** , seleccione **Guardar XMLFile. XML**.

     Se muestra el cuadro de diálogo **Guardar archivo como** .

7. Escriba el nombre del nuevo fragmento de código y seleccione **archivos de fragmento de código** en la ventana desplegable **Guardar como tipo** .

8. Use la lista desplegable **Guardar en** para cambiar la ubicación del archivo a la carpeta *Mis documentos\Visual Studio 2005 \ Code Snippets\XML\My XML Snippets* y, a continuación, presione **Guardar**.

## <a name="snippet-description"></a>Descripción del fragmento de código

En esta sección se describen algunos de los elementos principales del fragmento reutilizable. Para obtener más información sobre los elementos de esquema utilizados por los fragmentos XML, vea [referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>elemento SnippetType

El editor admite dos tipos de fragmentos:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

El tipo de `Expansion` determina si el fragmento de código aparece al invocar el comando **Insertar fragmento** . El tipo de `SurroundsWith` determina si el fragmento de código aparece al invocar el comando **rodear con** .

### <a name="code-element"></a>elemento de código

El elemento `Code` define el texto XML que se insertará cuando se invoque el fragmento.

> [!NOTE]
> El texto del fragmento XML se debe incluir en una sección `<![CDATA[...]]>`.

Este es el elemento `Code` que crea el fragmento reutilizable.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

El elemento `Code` incluye tres variables.

- $name$ es una variable definida por el usuario. Crea un elemento `name`, que tiene un valor editable que adopta "name" como valor predeterminado. Las variables definidas por el usuario se definen mediante el elemento `Literal`.

- $selected$ es una variable predefinida. Representa el texto que se seleccionó en el editor XML antes de invocar el fragmento de código. La colocación de esta variable determina dónde aparece el texto seleccionado en el fragmento de código que rodea esa selección.

- $end$ es una variable predefinida. Cuando el usuario presiona **entrar** para terminar de editar los campos de fragmentos de código, esta variable determina dónde se mueve el símbolo de intercalación (^).

  El elemento `Code` anterior inserta el siguiente texto XML:

```xml
<test>
  <name>name</name>
</test>
```

El valor del elemento name se marca como una región editable.

### <a name="literal-element"></a>elemento Literal

El elemento `Literal` se utiliza para identificar el texto de sustitución que se puede personalizar una vez que se ha insertado en el archivo. Por ejemplo, las cadenas de literales, los valores numéricos y algunos nombres de variables se pueden declarar como literales. Se puede definir un número cualquiera de literales en el fragmento XML y hacer referencia a ellos varias veces desde dentro del fragmento. A continuación se muestra un ejemplo de un elemento `Literal` que define una variable $name$ cuyo valor predeterminado es "name".

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Los literales también pueden hacer referencia a funciones. El editor XML incluye una función denominada **LookupPrefix**. La función **LookupPrefix** busca el URI de espacio de nombres especificado desde la ubicación del documento XML desde la que se invoca este fragmento de código y devuelve el prefijo de espacio de nombres definido para ese espacio de nombres, si existe, e incluye los dos puntos (:) en ese nombre. El siguiente es un ejemplo de un elemento `Literal` que utiliza la función **LookupPrefix** .

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

Luego, la variable $prefix$ puede utilizarse en cualquier parte del fragmento XML.

## <a name="see-also"></a>Vea también

- [Fragmentos de código XML](../xml-tools/xml-snippets.md)
- [Cómo: usar fragmentos de código XML](../xml-tools/how-to-use-xml-snippets.md)
- [Cómo: generar un fragmento de código XML a partir de un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)

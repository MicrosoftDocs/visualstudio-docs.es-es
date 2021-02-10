---
title: Referencia de esquemas de fragmentos de código
description: Aprenda sobre el esquema XML de los fragmentos de código de IntelliSense y cómo puede usarlo para aumentar su propia productividad.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22a5d4543548c8ac927487c9f4e2c9d95ea3487e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842152"
---
# <a name="code-snippets-schema-reference"></a>Referencia de esquemas de fragmentos de código

Los fragmentos de código de IntelliSense son piezas de código ya creado y listo para insertarlo en la aplicación con Visual Studio. Puede aumentar la productividad proporcionando fragmentos de código que reduzcan la cantidad de tiempo empleado en escribir código repetitivo o buscar ejemplos. Puede utilizar el esquema XML de fragmentos de código de IntelliSense para crear sus propios fragmentos de código y agregar los fragmentos de código que Visual Studio ya incluye.

## <a name="assembly-element"></a>Elemento Assembly

Especifica el nombre del ensamblado al que el fragmento de código hace referencia.

El valor de texto del elemento **Assembly** puede ser bien el nombre descriptivo del ensamblado, como `System.dll`, o su nombre seguro, como `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference-element)|Contiene información sobre las referencias de ensamblado requeridas por el fragmento de código.|

Se requiere un valor de texto. Este texto especifica el ensamblado al que hace referencia el fragmento de código.

## <a name="author-element"></a>Elemento Author

Especifica el nombre del autor del fragmento. El **Administrador de fragmentos de código** muestra el nombre del fragmento de código almacenado en el elemento `Author` del fragmento de código.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Contiene información general sobre el fragmento de código.|

Se requiere un valor de texto. Este texto especifica al autor del fragmento de código.

## <a name="code-element"></a>Elemento de código

Proporciona un contenedor para los bloques de código cortos.

### <a name="keywords"></a>Palabras clave

Se pueden usar dos palabras reservadas en el texto del elemento `Code`: `$end$` y `$selected$`. `$end$` marca la ubicación en la que se coloca el cursor después de insertar el fragmento de código. `$selected$` representa el texto seleccionado en el documento que se insertará en el fragmento de código cuando se invoque. Por ejemplo, dado un fragmento de código que incluya:

```
$selected$ is a great color.
```

Si se selecciona la palabra "Blue" cuando el usuario invoca la plantilla, el resultado es:

```
Blue is a great color.
```

No puede usar `$end$` o `$selected$` más de una vez en un fragmento de código. Si lo hace, se reconoce solo la segunda instancia. Dado un fragmento de código que incluya:

```
$selected$ is a great color. I love $selected$.
```

Si se selecciona la palabra "Blue", el resultado es:

```
 is a great color. I love Blue.
```

El espacio inicial aparece porque hay un espacio entre `$selected$` y `is`.

Todas las demás palabras clave `$` se definen dinámicamente en las etiquetas `<Literal>` y `<Object>`.

A continuación se muestra la estructura del elemento Code:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Se requiere un valor de texto. Este texto especifica el código, junto con los literales y objetos, que se pueden usar cuando este fragmento de código se inserta en un archivo de código.

### <a name="attributes"></a>Atributos

Hay tres atributos disponibles para el elemento Code:

- **Language**: atributo _obligatorio_ que especifica el lenguaje del fragmento de código. El valor puede ser uno de los siguientes:

   |Valor|Descripción|
   |-----|-----------|
   |`VB`|Identifica un fragmento de código de Visual Basic.|
   |`CSharp`|Identifica un fragmento de código de C#.|
   |`CPP`|Identifica un fragmento de código de C++.|
   |`XAML`|Identifica un fragmento de código XAML.|
   |`XML`|Identifica un fragmento de código XML.|
   |`JavaScript`|Identifica un fragmento de código JavaScript.|
   |`TypeScript`|Identifica un fragmento de código TypeScript.|
   |`SQL`|Identifica un fragmento de código SQL.|
   |`HTML`|Identifica un fragmento de código HTML.|

- **Kind**: atributo _opcional_ que especifica el tipo de código que contiene el fragmento de código. El valor puede ser uno de los siguientes:

   |Valor|Descripción|
   |-----|-----------|
   |`method body`|Especifica que el fragmento de código es un cuerpo de método y, por consiguiente, se debe insertar dentro de una declaración de método.|
   |`method decl`|Especifica que el fragmento de código es un método y, por consiguiente, se debe insertar dentro de una clase o módulo.|
   |`type decl`|Especifica que el fragmento de código es un tipo y, por consiguiente, se debe insertar dentro de una clase, módulo o espacio de nombres.|
   |`file`|Especifica que el fragmento es un archivo de código completo. Estos fragmentos de código se pueden insertar solos en un archivo de código o dentro de un espacio de nombres.|
   |`any`|Especifica que el fragmento de código se puede insertar en cualquier parte. Esta etiqueta se utiliza para fragmentos de código que son independientes del contexto, como los comentarios.|

- **Delimiter**: atributo _opcional_ que especifica el delimitador usado para describir los literales y los objetos del código. De manera predeterminada, el delimitador es `$`.

### <a name="parent-element"></a>Elemento primario

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet-element)|Contiene las referencias, las importaciones, las declaraciones y el código para el fragmento de código.|

## <a name="codesnippet-element"></a>Elemento CodeSnippet

Permite especificar un encabezado y varios fragmentos de código de IntelliSense, que puede insertar en los archivos de código de Visual Studio.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Atributo|Descripción|
|---------------|-----------------|
|`Format`|Atributo necesario. Especifica la versión del esquema del fragmento de código. El atributo de formato debe ser una cadena en la sintaxis de x.x.x, donde cada "x" representa un valor numérico del número de versión. Visual Studio omitirá los fragmentos de código con atributos `Format` que no sea capaz de interpretar.|

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Elemento necesario. Contiene información general sobre el fragmento de código. En un fragmento de código debe haber uno y solo un elemento `Header`.|
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet-element)|Elemento necesario. Contiene el código que insertará Visual Studio. En un fragmento de código debe haber uno y solo un elemento `Snippet`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets-element)|Elemento raíz del esquema XML del fragmento de código.|

## <a name="codesnippets-element"></a>Elemento CodeSnippets

Agrupa elementos [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element). El elemento `CodeSnippets` es el elemento raíz del esquema XML del fragmento de código.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Elemento opcional. Elemento primario de todos los datos del fragmento de código. Puede haber cero o más elementos `CodeSnippet` en un elemento `CodeSnippets`.|

## <a name="declarations-element"></a>Elemento Declarations

Especifica los literales y los objetos que componen las partes de un fragmento de código que puede editar.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal-element)|Elemento opcional. Define los literales del fragmento de código que puede editar. Puede haber cero o más elementos `Literal` en un elemento `Declarations`.|
|[Elemento Object](../ide/code-snippets-schema-reference.md#object-element)|Elemento opcional. Define los objetos del fragmento de código modificable. Puede haber cero o más elementos `Object` en un elemento `Declarations`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet-element)|Contiene las referencias, las importaciones, las declaraciones y el código para el fragmento de código.|

## <a name="default-element"></a>Elemento Default

Especifica el valor predeterminado del literal o del objeto para un fragmento de código de IntelliSense.

```xml
<Default>
    Default value
</Default>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal-element)|Define los campos literales del fragmento de código que se pueden editar.|
|[Elemento Object](../ide/code-snippets-schema-reference.md#object-element)|Define los campos del objeto del fragmento de código que se pueden editar.|

Se requiere un valor de texto. Este texto especifica el valor predeterminado del literal o del objeto que ocupa los campos del fragmento de código que puede editar.

## <a name="description-element"></a>Elemento Description

Especifica información descriptiva acerca del contenido de un fragmento de código de IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Contiene información general sobre el fragmento de código.|

Se requiere un valor de texto. Este texto describe el fragmento de código.

## <a name="function-element"></a>Function, elemento

Especifica una función que se ejecutará cuando un literal o un objeto reciba foco en Visual Studio.

> [!NOTE]
> No todos los lenguajes admiten elementos `function`. Consulte la documentación específica del lenguaje sobre las funciones que están disponibles.

```xml
<Function>
    FunctionName
</Function>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal-element)|Define los campos literales del fragmento de código que se pueden editar.|
|[Elemento Object](../ide/code-snippets-schema-reference.md#object-element)|Define los campos del objeto del fragmento de código que se pueden editar.|

Se requiere un valor de texto. Este texto especifica una función que se ejecutará cuando el campo del literal u objeto reciba el foco en Visual Studio.

## <a name="header-element"></a>Elemento Header

Especifica información general acerca del fragmento de código de IntelliSense.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Author](../ide/code-snippets-schema-reference.md#author-element)|Elemento opcional. El nombre de la persona o compañía que creó el fragmento de código. Puede haber cero o un elemento `Author` en un elemento `Header`.|
|[Elemento Description](../ide/code-snippets-schema-reference.md#description-element)|Elemento opcional. Descripción del fragmento de código. Puede haber cero o un elemento `Description` en un elemento `Header`.|
|[Elemento HelpUrl](../ide/code-snippets-schema-reference.md#helpurl-element)|Elemento opcional. Dirección URL que contiene más información sobre el fragmento de código. Puede haber cero o un elemento `HelpURL` en un elemento Header. **Nota:**  Visual Studio no utiliza el elemento `HelpUrl`. El elemento forma parte del esquema XML de fragmentos de código de IntelliSense y cualquier fragmento de código que contenga el elemento se validará, pero el valor del elemento no se utilizará nunca.|
|[Elemento Keywords](../ide/code-snippets-schema-reference.md#keywords-element)|Elemento opcional. Agrupa los elementos `Keyword`. Puede haber cero o un elemento `Keywords` en un elemento `Header`.|
|[Elemento Shortcut](../ide/code-snippets-schema-reference.md#shortcut-element)|Elemento opcional. Especifica el texto de acceso directo que se puede utilizar para insertar el fragmento. Puede haber cero o un elemento `Shortcut` en un elemento `Header`.|
|[Elemento SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Elemento opcional. Agrupa los elementos `SnippetType`. Puede haber cero o un elemento `SnippetTypes` en un elemento `Header`. Si no hay ningún elemento `SnippetTypes`, el fragmento de código siempre es válido.|
|[Elemento Title](../ide/code-snippets-schema-reference.md#title-element)|Elemento necesario. Nombre descriptivo del fragmento de código. Debe haber uno y solo un elemento `Title` en un elemento `Header`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Elemento primario de todos los datos del fragmento de código.|

## <a name="helpurl-element"></a>Elemento HelpUrl

Especifica una dirección URL que proporciona más información acerca de un fragmento de código.

> [!NOTE]
> Visual Studio no utiliza el elemento `HelpUrl`. El elemento forma parte del esquema XML de fragmentos de código de IntelliSense y cualquier fragmento de código que contenga el elemento se validará, pero el valor del elemento no se utilizará nunca.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Contiene información general sobre el fragmento de código.|

El valor de texto es opcional. Este texto especifica la dirección URL que se puede visitar para obtener mas información sobre un fragmento de código.

## <a name="id-element"></a>Elemento ID

Especifica un identificador único para un elemento `Literal` u `Object`. Dos literales u objetos en el mismo fragmento de código no pueden tener el mismo valor de texto en sus elementos `ID`. Los literales y objetos no pueden contener un elemento `ID` con un valor end. El valor `$end$` está reservado y se utiliza para marcar la ubicación en que se coloca el cursor después de insertar el fragmento de código.

```xml
<ID>
    Unique Identifier
</ID>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal-element)|Define los campos literales del fragmento de código que se pueden editar.|
|[Elemento Object](../ide/code-snippets-schema-reference.md#object-element)|Define los campos del objeto del fragmento de código que se pueden editar.|

Se requiere un valor de texto. Este texto especifica el identificador único del objeto o literal.

## <a name="import-element"></a>Elemento Import

Especifica los espacios de nombres importados utilizados por un fragmento de código de IntelliSense.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Namespace](../ide/code-snippets-schema-reference.md#namespace-element)|Elemento necesario. Especifica el espacio de nombres utilizado por el fragmento de código. Debe haber uno y solo un elemento `Namespace` en un elemento `Import`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Imports](../ide/code-snippets-schema-reference.md#imports-element)|Elemento grouping de los elementos **Import**.|

## <a name="imports-element"></a>Elemento Imports

Agrupa los elementos `Import` individuales.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Import](../ide/code-snippets-schema-reference.md#import-element)|Elemento opcional. Contiene los espacios de nombres importados para el fragmento de código. Puede haber cero o más elementos **Import** en un elemento `Imports`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet-element)|Contiene las referencias, las importaciones, las declaraciones y el código para el fragmento de código.|

## <a name="keyword-element"></a>Elemento Keyword

Especifica una palabra clave personalizada para el fragmento de código. Visual Studio utiliza las palabras clave del fragmento de código. Los proveedores de contenido en línea utilizan este método estándar para agregar palabras clave personalizadas para la búsqueda o clasificación.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Keywords](../ide/code-snippets-schema-reference.md#keywords-element)|Agrupa los elementos `Keyword` individuales.|

Se requiere un valor de texto. La palabra clave del fragmento de código.

## <a name="keywords-element"></a>Elemento Keywords

Agrupa los elementos `Keyword` individuales. Visual Studio utiliza las palabras clave del fragmento de código. Los proveedores de contenido en línea utilizan este método estándar para agregar palabras clave personalizadas para la búsqueda o clasificación.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Keyword](../ide/code-snippets-schema-reference.md#keyword-element)|Elemento opcional. Contiene palabras clave individuales para el fragmento de código. Puede haber cero o más elementos `Keyword` en un elemento `Keywords`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Contiene información general sobre el fragmento de código.|

## <a name="literal-element"></a>elemento Literal

Define los literales del fragmento de código que puede editar. El elemento `Literal` se utiliza para identificar el reemplazo de una pieza de código que está incluida completamente en el fragmento, pero que es probable que se personalice tras insertarla en el código. Por ejemplo, las cadenas literales, los valores numéricos y algunos nombres de variables se deben declarar como literales.

Los literales y objetos no pueden contener un elemento **ID** con un valor selected o end. El valor `$selected$` representa el texto seleccionado en el documento que se insertará en el fragmento de código cuando se invoque. `$end$` marca la ubicación en la que se coloca el cursor después de insertar el fragmento de código.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Atributo|Descripción|
|---------------|-----------------|
|`Editable`|Atributo `Boolean` opcional. Especifica si puede o no editar el literal después de insertar el fragmento de código. El valor predeterminado de este atributo es `true`.|

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Default](../ide/code-snippets-schema-reference.md#default-element)|Elemento necesario. Especifica el valor predeterminado del literal cuando inserta el fragmento de código. Debe haber uno y solo un elemento `Default` en un elemento `Literal`.|
|[Elemento Function](../ide/code-snippets-schema-reference.md#function-element)|Elemento opcional. Especifica una función que se ejecuta cuando el literal recibe el foco en Visual Studio. Puede haber cero o un elemento `Function` en un elemento `Literal`.|
|[Elemento ID](../ide/code-snippets-schema-reference.md#id-element)|Elemento necesario. Especifica un identificador único para el literal. Debe haber uno y solo un elemento `ID` en un elemento `Literal`.|
|[Elemento ToolTip](../ide/code-snippets-schema-reference.md#tooltip-element)|Elemento opcional. Describe el valor esperado y el uso del literal. Puede haber cero o un elemento **Tooltip** en un elemento `Literal`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Contiene los literales y objetos de un fragmento de código que se pueden editar.|

## <a name="namespace-element"></a>Elemento Namespace

Especifica el espacio de nombres que se debe importar para compilar y ejecutar el fragmento de código. Si no existe aún, el espacio de nombres especificado en el elemento `Namespace` se agrega automáticamente a una directiva `using` o a una instrucción `Imports` al comienzo del código.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Import](../ide/code-snippets-schema-reference.md#import-element)|Importa el espacio de nombres especificado.|

Se requiere un valor de texto. Este texto especifica un espacio de nombres que el fragmento de código presupone que se ha importado.

## <a name="object-element"></a>Elemento Object

Define los objetos del fragmento de código modificable. El elemento `Object` se utiliza para identificar un elemento necesario para el fragmento de código, pero que probablemente se defina fuera del propio fragmento. Por ejemplo, los controles de Windows Forms, los controles de ASP.NET, las instancias de objeto y las instancias de tipo se deberían declarar como objetos. Las declaraciones de objeto requieren que se especifique un tipo, lo que se hace mediante el elemento `Type`.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Atributo|Descripción|
|---------------|-----------------|
|`Editable`|Atributo `Boolean` opcional. Especifica si puede o no editar el literal después de insertar el fragmento de código. El valor predeterminado de este atributo es `true`.|

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Default](../ide/code-snippets-schema-reference.md#default-element)|Elemento necesario. Especifica el valor predeterminado del literal cuando inserta el fragmento de código. Debe haber uno y solo un elemento `Default` en un elemento `Literal`.|
|[Elemento Function](../ide/code-snippets-schema-reference.md#function-element)|Elemento opcional. Especifica una función que se ejecuta cuando el literal recibe el foco en Visual Studio. Puede haber cero o un elemento `Function` en un elemento `Literal`.|
|[Elemento ID](../ide/code-snippets-schema-reference.md#id-element)|Elemento necesario. Especifica un identificador único para el literal. Debe haber uno y solo un elemento `ID` en un elemento `Literal`.|
|[Elemento ToolTip](../ide/code-snippets-schema-reference.md#tooltip-element)|Elemento opcional. Describe el valor esperado y el uso del literal. Puede haber cero o un elemento **Tooltip** en un elemento `Literal`.|
|[Elemento Type](../ide/code-snippets-schema-reference.md#type-element)|Elemento necesario. Especifica el tipo del objeto. Debe haber uno y solo un elemento `Type` en un elemento `Object`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Contiene los literales y objetos de un fragmento de código que se pueden editar.|

## <a name="reference-element"></a>Elemento Reference

Especifica información sobre las referencias a ensamblados que requiere el fragmento de código.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Assembly](../ide/code-snippets-schema-reference.md#assembly-element)|Elemento necesario. Contiene el nombre del ensamblado al que hace referencia el fragmento de código. Debe haber uno y solo un elemento `Assembly` en un elemento `Reference`.|
|[Elemento Url](../ide/code-snippets-schema-reference.md#url-element)|Elemento opcional. Contiene una dirección URL que proporciona más información sobre el ensamblado al que se hace referencia. Puede haber cero o un elemento `Url` en un elemento `Reference`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento References](../ide/code-snippets-schema-reference.md#references-element)|Elemento de agrupación de los elementos `Reference`.|

## <a name="references-element"></a>Elemento References

Agrupa los elementos `Reference` individuales.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference-element)|Elemento opcional. Contiene información sobre referencias de ensamblado para el fragmento de código. Puede haber cero o más elementos `Reference` en un elemento `References`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Snippet](../ide/code-snippets-schema-reference.md#snippet-element)|Contiene las referencias, las importaciones, las declaraciones y el código para el fragmento de código.|

## <a name="shortcut-element"></a>Elemento Shortcut

Especifica el texto de acceso directo utilizado para insertar el fragmento de código. El valor de texto de un elemento `Shortcut` solo puede contener caracteres alfanuméricos, guiones ( - ) y caracteres de subrayado ( _ ).

> [!CAUTION]
> El subrayado (_) no es un carácter admitido en accesos directos de fragmentos de código de C++.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Contiene información general sobre el fragmento de código.|

El valor de texto es opcional. Este texto se utiliza como método abreviado para insertar el fragmento de código.

## <a name="snippet-element"></a>Elemento Snippet

Especifica las referencias, las importaciones, las declaraciones y el código para el fragmento de código.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento Code](../ide/code-snippets-schema-reference.md#code-element)|Elemento necesario. Especifica el código que desea insertar en un archivo de documentación. Debe haber uno y solo un elemento `Code` en un elemento `Snippet`.|
|[Elemento Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Elemento opcional. Especifica los literales y los objetos que componen las partes de un fragmento de código que puede editar. Puede haber cero o un elemento `Declarations` en un elemento `Snippet`.|
|[Elemento Imports](../ide/code-snippets-schema-reference.md#imports-element)|Elemento opcional. Agrupa los elementos `Import` individuales. Puede haber cero o un elemento `Imports` en un elemento `Snippet`.|
|[Elemento References](../ide/code-snippets-schema-reference.md#references-element)|Elemento opcional. Agrupa los elementos `Reference` individuales. Puede haber cero o un elemento `References` en un elemento `Snippet`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Permite especificar un encabezado y varios fragmentos de código de IntelliSense, que puede insertar en los archivos de código de Visual Studio.|

## <a name="snippettype-element"></a>elemento SnippetType

Especifica la manera en que Visual Studio inserta el fragmento de código.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Agrupa los elementos `SnippetType`.|

El valor de texto debe uno de los valores siguientes.

- `SurroundsWith`: permite colocar el fragmento de código alrededor de una parte de código seleccionada.

- `Expansion`: permite insertar el fragmento de código donde se encuentra el cursor.

- `Refactoring`: especifica que el fragmento de código se usará durante la refactorización de C#. `Refactoring` no se puede usar en fragmentos de código personalizados.

## <a name="snippettypes-element"></a>Elemento SnippetTypes

Agrupa los elementos `SnippetType` individuales. Si el elemento `SnippetTypes` no está presente, el fragmento de código se puede insertar en cualquier parte del código.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Elemento secundario|Descripción|
|-------------------|-----------------|
|[Elemento SnippetType](../ide/code-snippets-schema-reference.md#snippettype-element)|Elemento opcional. Especifica la manera en que Visual Studio inserta el fragmento en el código. Puede haber cero o más elementos `SnippetType` en un elemento `SnippetTypes`.|

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Especifica información general sobre el fragmento de código.|

## <a name="title-element"></a>Elemento Title

Especifica el título del fragmento de código. El título almacenado en el elemento `Title` del fragmento de código aparece en el **Selector de fragmentos de código** y en la descripción del fragmento de código del **Administrador de fragmentos de código**.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Header](../ide/code-snippets-schema-reference.md#header-element)|Especifica información general sobre el fragmento de código.|

Se requiere un valor de texto. Este texto especifica el título del fragmento de código.

## <a name="tooltip-element"></a>Elemento ToolTip

Describe el valor y el uso esperados de un literal o de un objeto de un fragmento de código, que Visual Studio muestra como información sobre herramientas cuando inserta el fragmento de código en un proyecto. El texto del elemento ToolTip se muestra cuando el mouse se desplaza sobre el literal u objeto después de que se haya insertado el fragmento de código.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Literal](../ide/code-snippets-schema-reference.md#literal-element)|Define los campos literales del fragmento de código que se pueden editar.|
|[Elemento Object](../ide/code-snippets-schema-reference.md#object-element)|Define los campos del objeto del fragmento de código que se pueden editar.|

Se requiere un valor de texto. Este texto especifica la descripción de ToolTip que se va a asociar al objeto o literal en el fragmento de código.

## <a name="type-element"></a>Elemento Type

Especifica el tipo del objeto. El elemento `Object` se utiliza para identificar un elemento necesario para el fragmento de código, pero que probablemente se defina fuera del propio fragmento. Por ejemplo, los controles de Windows Forms, los controles de ASP.NET, las instancias de objeto y las instancias de tipo se deberían declarar como objetos. Las declaraciones de objeto requieren que se especifique un tipo, lo que se hace mediante el elemento `Type`.

```xml
<Type>
    Type
</Type>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Object](../ide/code-snippets-schema-reference.md#object-element)|Define los campos del objeto del fragmento de código que se pueden editar.|

Se requiere un valor de texto. Este texto especifica el tipo del objeto. Por ejemplo:

```xml
<Type>System.Data.SqlClient.SqlConnection</Type>
```

## <a name="url-element"></a>Elemento Url

Especifica una dirección URL que proporciona más información acerca del ensamblado al que se hace referencia.

> [!NOTE]
> El elemento `Url` solo se admite para los proyectos de Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Elemento primario|Descripción|
| - |-----------------|
|[Elemento Reference](../ide/code-snippets-schema-reference.md#reference-element)|Especifica las referencias a ensamblados que requiere el fragmento de código.|

Se requiere un valor de texto. Este texto especifica una dirección URL con más información sobre el ensamblado al que se ha hecho referencia. Esta dirección URL se muestra cuando la referencia no se puede agregar al proyecto.

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../ide/code-snippets.md)
- [Tutorial: Creación de un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md)

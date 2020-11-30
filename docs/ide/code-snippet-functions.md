---
title: Funciones de los fragmentos de código
description: Aprenda sobre las funciones GenerateSwitchCases(EnumerationLiteral), ClassName() y SimpleTypeName(TypeName) que están disponibles para usar con fragmentos de código de C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6529f4f82f7a8a6862ae85adbf170d2fb6f8706
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006515"
---
# <a name="code-snippet-functions"></a>Funciones de los fragmentos de código

Hay tres funciones disponibles para utilizar con fragmentos de código de C#. Las funciones se especifican en el elemento [Function](../ide/code-snippets-schema-reference.md#function-element) del fragmento de código. Para obtener información sobre cómo crear fragmentos de código, vea [Fragmentos de código](../ide/code-snippets.md).

## <a name="functions"></a>Functions

En la tabla siguiente se describen las funciones que puede utilizar con el elemento `Function` en fragmentos de código.

|Función|Descripción|Idioma|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Genera una instrucción switch y un conjunto de instrucciones case para los miembros de la enumeración especificada por el parámetro `EnumerationLiteral`. El parámetro `EnumerationLiteral` debe ser una referencia a un literal de enumeración o un tipo de enumeración.|C#|
|`ClassName()`|Devuelve el nombre de la clase que contiene el fragmento de código insertado.|C#|
|`SimpleTypeName(TypeName)`|Reduce el parámetro *TypeName* a su forma más sencilla en el contexto en que se invocó el fragmento de código.|C#|

## <a name="generateswitchcases-example"></a>Ejemplo de GenerateSwitchCases

En el ejemplo siguiente se muestra cómo usar la función `GenerateSwitchCases`. Cuando se inserta este fragmento de código y se especifica una enumeración en el literal `$switch_on$`, el literal `$cases$` genera una instrucción `case` para cada valor de la enumeración.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="classname-example"></a>Ejemplo de ClassName

En el ejemplo siguiente se muestra cómo usar la función `ClassName`. Cuando se inserta este fragmento de código, el literal `$classname$` se reemplaza con el nombre de la clase envolvente en esa ubicación del archivo de código.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="simpletypename-example"></a>Ejemplo de SimpleTypeName

En este ejemplo se muestra cómo utilizar la función `SimpleTypeName`. Al insertar este fragmento de código en un archivo de código, el literal `$SystemConsole$` se reemplaza por la forma más sencilla del tipo <xref:System.Console> en el contexto en el que se invocó el fragmento de código.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Consulte también

- [Elemento Function](../ide/code-snippets-schema-reference.md#function-element)
- [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)

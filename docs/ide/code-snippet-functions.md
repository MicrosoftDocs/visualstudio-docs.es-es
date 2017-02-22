---
title: "Funciones de los fragmentos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fragmentos de código [Visual Studio], funciones"
  - "fragmentos de código de IntelliSense, funciones"
  - "fragmentos [Visual Studio], funciones"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Funciones de los fragmentos de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay tres funciones disponibles para su uso con fragmentos de código de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Las funciones se especifican en el elemento [Function](http://msdn.microsoft.com/es-es/572c5549-5821-4e15-8ecd-0fa86c1c65df) del fragmento de código.  Para obtener información sobre cómo crear fragmentos de código, vea [Fragmentos de código](../ide/code-snippets.md).  
  
## Funciones  
 En la tabla siguiente se describen las funciones disponibles para su uso con el elemento `Function` en fragmentos de código.  
  
|Función|Descripción|Language|  
|-------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Genera una instrucción switch y un conjunto de instrucciones case para los miembros de la enumeración especificados por el parámetro `EnumerationLiteral`.  El parámetro `EnumerationLiteral` debe ser una referencia a un literal de enumeración o a un tipo de enumeración.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Devuelve el nombre de la clase que contiene el fragmento de código insertado.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Reduce el parámetro *TypeName* a su forma más simple en el contexto en el que se invocó el fragmento de código.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar la función `GenerateSwitchCases`.  Si se inserta este fragmento de código y se especifica una enumeración en el literal `$switch_on$`, el literal `$cases$` generará una instrucción `case` por cada valor de la enumeración.  
  
```  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar la función `ClassName`.  Cuando se inserta este fragmento de código, el literal `$classname$` se reemplaza por el nombre de la clase envolvente en dicha ubicación del archivo de código.  
  
```  
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
            <Code Language="vjsharp" Format="CData">  
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
  
## Ejemplo  
 En este ejemplo se muestra cómo utilizar la función `SimpleTypeName`.  Cuando se inserta este fragmento de código en un archivo de código, el literal `$SystemConsole$` se reemplaza por la forma más simple del tipo <xref:System.Console> en el contexto en el que se invocó el fragmento de código.  
  
```  
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
  
## Vea también  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/es-es/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)
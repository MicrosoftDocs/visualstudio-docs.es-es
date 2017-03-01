---
title: "Configuración de estilo de código .NET para Editorconfig | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
author: kaseyu
ms.author: kaseyu
manager: davidcsa
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 31f433b28b67dc6f3179be87cb5894b5b3f0aa4f
ms.openlocfilehash: e0fcd94f2e42f2ce8d454b9d754cfa4ad063d9e0
ms.lasthandoff: 02/22/2017

---

# <a name="net-code-style-settings-for-editorconfig"></a>Configuración de estilo de código .NET para Editorconfig

## <a name="possible-values"></a>Valores posibles

`options_name = false|true : none|suggestion|warning|error`

Para la opción de estilo de código, debe especificar **true** (se prefiere esta opción) o **false** (no se prefiere esta opción), dos puntos (`:`) y una gravedad (`none`, `suggestion`, `warning` o `error`). La gravedad hace referencia al nivel de cumplimiento de ese estilo que quiere en su código base.

Gravedad | Efecto
------------ | -------------
ninguna | No muestra nada al usuario cuando este estilo no se sigue, pero las características de generación de código se generarán en este estilo. 
suggestion | Cuando este estilo no se sigue, se muestra al usuario como una sugerencia (puntos subyacentes en los dos primeros caracteres).
warning | Cuando este estilo no se sigue, se muestra una advertencia del compilador.
error | Cuando este estilo no se sigue, se muestra un error del compilador.

## <a name="net-code-style-options"></a>Opciones de estilo de código .NET

- [Configuración del estilo de código DotNet](#this_and_me)
    - [Cualificación "This." y "Me."](#this_and_me)
        - [Campos](#this_and_me_fields)
        - [Propiedades](#this_and_me_properties)
        - [Métodos](#this_and_me_methods)
        - [Eventos](#this_and_me_events)
    - [Palabras clave del lenguaje (int, string, etc.) frente a nombres de tipos de marco para referencias de tipo](#language_keywords)
        - [Variables locales, parámetros y miembros](#language_keywords_variables)
        - [Expresiones de acceso a miembros](#language_keywords_member_access)
    - [Preferencias de nivel de expresión](#expression_level)
        - [Inicializadores de objeto](#expression_level_object_initializers)
        - [Inicializadores de colección](#expression_level_collection_initializers)
        - [Nombres de tupla explícitos](#expression_level_tuple_names)
        - [Expresiones de fusión en la comprobación de "NULL"](#expression_level_null_checking)
        - [Propagación de tipo NULL en la comprobación de "NULL"](#expression_level_null_propogation)
- [Configuración del estilo de código CSharp](#csharp_codestyle)
    - ["var"](#var)
        - ["var" para tipos integrados](#var_built_in)
        - ["var" cuando el tipo es aparente](#var_apparent)
        - ["var" en otro sitio](#var_elsewhere)
    - [Miembros con forma de expresión](#expression_bodied_members)
        - [Métodos](#expression_bodied_members_methods)
        - [Constructores](#expression_bodied_members_constructors)
        - [Operadores](#expression_bodied_members_operators)
        - [Propiedades](#expression_bodied_members_properties)
        - [Indizadores](#expression_bodied_members_indexers)
        - [Descriptores de acceso](#expression_bodied_members_accessors)
    - [Coincidencia de patrones](#pattern_matching)
        - ["is" con la comprobación de "conversión"](#pattern_matching_is_cast)
        - ["as" con la comprobación de "NULL"](#pattern_matching_as_null)
    - [Declaraciones de variables insertadas](#inlined_variable_declarations)
    - [Preferencias de la comprobación de "NULL"](#null_checking)
        - [Expresiones Throw](#null_checking_throw_expressions)
        - [Llamadas de delegado condicionales](#null_checking_conditional_delegate_calls)

## <a name="a-namethisandmethis-and-me-qualificationa"></a><a name="this_and_me">Cualificación "This." y "Me."</a>

### <a name="a-namethisandmefieldsfieldsa"></a><a name="this_and_me_fields">Campos</a>

|  Nombre de la opción | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todos los campos no estáticos que se han usado en métodos no estáticos comiencen por `this.` en C# o por `Me.` en Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** `Me.capacity = 0`
| False | Prefiere que todos los campos no estáticos que se han usado en métodos no estáticos no comiencen por `this.` en C# ni por `Me.` en Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** `capacity = 0`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="a-namethisandmepropertiespropertiesa"></a><a name="this_and_me_properties">Propiedades</a>

|  Nombre de la opción | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todas las propiedades no estáticas que se han usado en métodos no estáticos comiencen por `this.` en C# o por `Me.` en Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** `Me.ID = 0`
| False | Prefiere que todas las propiedades no estáticas que se han usado en métodos no estáticos *no* comiencen por `this.` en C# ni por `Me.` en Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** `ID = 0`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="a-namethisandmemethodsmethodsa"></a><a name="this_and_me_methods">Métodos</a>
|  Nombre de la opción | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todos los métodos no estáticos que se han llamado desde métodos no estáticos comiencen por `this.` en C# y por `Me.` en VB.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** `Me.Display()`
| False | Prefiere que todos los métodos no estáticos que se han llamado desde métodos no estáticos *no* comiencen por `this.` en C# ni por `Me.` en VB. | **C#:** <br>`Display();` <br><br> **Visual Basic:** `Display()`


#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="a-namethisandmeeventseventsa"></a><a name="this_and_me_events">Eventos</a>
|  Nombre de la opción | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todos los eventos no estáticos a los que se hace referencia desde métodos no estáticos comiencen por `this.` en C# y por `Me.` en VB.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Me.Elapsed, AddressOf Handler`
| False | Prefiere que todos los eventos no estáticos a los que se hace referencia desde métodos no estáticos *no* comiencen por `this.` en C# ni por `Me.` en VB. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Palabras clave del lenguaje (int, string, etc.) frente a nombres de tipos de marco para referencias de tipo </a>
### <a name="a-namelanguagekeywordsvariableslocals-parameters-and-membersa"></a><a name="language_keywords_variables">Variables locales, parámetros y miembros</a>
|  Nombre de la opción | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Para variables locales, parámetros y miembros de tipo, prefiere tipos que tengan una palabra clave del lenguaje para representarlos (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar la palabra clave en lugar del nombre de tipo (`Int32`, `Int64`, etc.).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Para variables locales, parámetros y miembros de tipo, prefiere tipos que tengan una palabra clave del lenguaje para representarlos (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar el nombre de tipo (`Int32`, `Int64`, etc.) en lugar de la palabra clave.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="a-namelanguagekeywordsmemberaccessmember-access-expressionsa"></a><a name="language_keywords_member_access">Expresiones de acceso a miembros</a>
|  Nombre de la opción | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere la palabra clave siempre que una expresión de acceso a miembros se use en un tipo con una representación de palabra clave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** `Dim local = Integer.MaxValue`
| False | Prefiere el nombre de tipo siempre que una expresión de acceso a miembros se use en un tipo con una representación de palabra clave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="a-nameexpressionlevelexpression-level-preferencesa"></a><a name="expression_level">Preferencias de nivel de expresión</a>
### <a name="a-nameexpressionlevelobjectinitializersobject-initializersa"></a><a name="expression_level_object_initializers">Inicializadores de objeto</a>
|  Nombre de la opción | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que los objetos se inicialicen con inicializadores de objeto siempre que sea posible.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** `Dim c = New Customer() With { .Age = 21 }`
| False | Prefiere que los objetos *no* se inicialicen con inicializadores de objeto. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="a-nameexpressionlevelcollectioninitializerscollection-initializersa"></a><a name="expression_level_collection_initializers">Inicializadores de colección</a>
|  Nombre de la opción | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que las colecciones se inicialicen con inicializadores de colección siempre que sea posible.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Prefiere que las colecciones *no* se inicialicen con inicializadores de colección. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="a-nameexpressionleveltuplenamesexplicit-tuple-namesa"></a><a name="expression_level_tuple_names">Nombres de tupla explícitos</a>
|  Nombre de la opción | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere nombres de tupla a propiedades ItemX.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Prefiere propiedades ItemX a nombres de tupla. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="a-nameexpressionlevelnullcheckingcoalescing-expressions-in-null-checkinga"></a><a name="expression_level_null_checking">Expresiones de fusión en la comprobación de "NULL"</a>
|  Nombre de la opción | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere la expresión de fusión NULL a la comprobación del operador ternario.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Prefiere la comprobación del operador ternario a la expresión de fusión NULL. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="a-nameexpressionlevelnullpropogationnull-propagation-in-null-checkinga"></a><a name="expression_level_null_propogation">Propagación de tipo NULL en la comprobación de "NULL"</a>
|  Nombre de la opción | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere usar el operador condicional NULL siempre que sea posible.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Prefiere usar la comprobación NULL ternaria siempre que sea posible. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="a-namecsharpcodestylecsharp-code-style-settingsa"></a><a name="csharp_codestyle">Configuración del estilo de código CSharp</a>
## <a name="a-namevarvara"></a><a name="var">"var"</a>
### <a name="a-namevarbuiltinvar-for-built-in-typesa"></a><a name="var_built_in">"var" para tipos integrados</a>
|  Nombre de la opción | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que se use `var` para los tipos de sistema integrados como `int`.| **C#:** <br>`var x = 5;`
| False | Prefiere que no se use `var` para los tipos de sistema integrados como `int`. | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="a-namevarapparentvar-when-type-is-apparenta"></a><a name="var_apparent">"var" cuando el tipo es aparente</a>
|  Nombre de la opción | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere `var` cuando el tipo ya se ha mencionado en el lateral derecho de una expresión de declaración.| **C#:** <br>`var obj = new C();`
| False | Prefiere no usar `var` cuando el tipo ya se ha mencionado en el lateral derecho de una expresión de declaración. | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="a-namevarelsewherevar-elsewherea"></a><a name="var_elsewhere">"var" en otro sitio</a>
|  Nombre de la opción | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere `var` en todos los casos, a no ser que otra regla de estilo de código lo reemplace.| **C#:** <br>`var f = this.Init();`
| False | Prefiere no usar var en todos los casos, a no ser que otra regla de estilo de código lo reemplace.| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

### <a name="a-nameexpressionbodiedmembersmethodsa"></a><a name="expression_bodied_members">Métodos</a>
|  Nombre de la opción | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere miembros con forma de expresión para los métodos.| **C#:** <br>`public int GetAge() => this.Age;`
| False | No prefiere miembros con forma de expresión para los métodos.| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="a-nameexpressionbodiedmembersconstructorsconstructorsa"></a><a name="expression_bodied_members_constructors">Constructores</a>
|  Nombre de la opción | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere miembros con forma de expresión para los constructores.| **C#:** <br>`public Customer(int age) => Age = age;`
| False | No prefiere miembros con forma de expresión para los constructores.| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="a-nameexpressionbodiedmembersoperatorsoperatorsa"></a><a name="expression_bodied_members_operators">Operadores</a>
|  Nombre de la opción | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere miembros con forma de expresión para los operadores.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | No prefiere miembros con forma de expresión para los operadores.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="a-nameexpressionbodiedmemberspropertiespropertiesa"></a><a name="expression_bodied_members_properties">Propiedades</a>
|  Nombre de la opción | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere miembros con forma de expresión para las propiedades.| **C#:** <br>`public int Age => _age;`
| False | No prefiere miembros con forma de expresión para las propiedades.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="a-nameexpressionbodiedmembersindexersindexersa"></a><a name="expression_bodied_members_indexers">Indizadores</a>
|  Nombre de la opción | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere miembros con forma de expresión para los indexadores.| **C#:** <br>`public T this[int i] => _value[i];`
| False | No prefiere miembros con forma de expresión para los indexadores.| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="a-nameexpressionbodiedmembersaccessorsaccessorsa"></a><a name="expression_bodied_members_accessors">Descriptores de acceso</a>
|  Nombre de la opción | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere miembros con forma de expresión para los descriptores de acceso.| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | No prefiere miembros con forma de expresión para los descriptores de acceso.| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="a-namepatternmatchingpattern-matchinga"></a><a name="pattern_matching">Coincidencia de patrones</a>
### <a name="a-namepatternmatchingiscastis-with-cast-checkinga"></a><a name="pattern_matching_is_cast">"is" con la comprobación de "conversión"</a>
|  Nombre de la opción | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere la coincidencia de patrones en lugar de expresiones `is` con conversiones de tipo.| **C#:** <br>`if (o is int i) {...}`
| False | Prefiere expresiones `is` con conversiones de tipo en lugar de la coincidencia de patrones.| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="a-namepatternmatchingasnullas-with-null-checkinga"></a><a name="pattern_matching_as_null">"as" con la comprobación de "NULL"</a>
|  Nombre de la opción | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere la coincidencia de patrones en lugar de expresiones `as` con comprobaciones NULL para determinar si algo es de un tipo determinado.| **C#:** <br>`if (o is string s) {...}`
| False | Prefiere expresiones `as` con comprobaciones NULL en lugar de la coincidencia de patrones para determinar si algo es de un tipo determinado.| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="a-nameinlinedvariabledeclarationsinlined-variable-declarationsa"></a><a name="inlined_variable_declarations">Declaraciones de variables insertadas</a>
|  Nombre de la opción | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere variables `out` que se declaren como inline siempre que sea posible. | **C#:** <br>`if (int.TryParse(value out int i) {...}`
| False | Prefiere variables `out` que se declaren explícitamente.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

## <a name="a-namenullcheckingnull-checking-preferencesa"></a><a name="null_checking">Preferencias de la comprobación de "NULL"</a>
### <a name="a-namenullcheckingthrowexpressionsthrow-expressionsa"></a><a name="null_checking_throw_expressions">Expresiones Throw</a>
|  Nombre de la opción | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere usar expresiones Throw en lugar de instrucciones Throw. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Prefiere usar instrucciones Throw en lugar de expresiones Throw.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="a-namenullcheckingconditionaldelegatecallsprefer-conditional-delegate-callsa"></a><a name="null_checking_conditional_delegate_calls">Preferir llamadas de delegado condicionales</a>
|  Nombre de la opción | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere usar la operación de fusión condicional (`?.`) cuando se invoque a Lambda en lugar de realizar una comprobación de NULL. | **C#:** <br>`func?.Invoke(args);`
| False | Prefiere realizar una comprobación de NULL antes de invocar a Lambda en lugar de usar el operador de fusión condicional (`?.`).| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```


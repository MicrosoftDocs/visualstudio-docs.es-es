---
title: "Configuración de la convención de codificación de .NET para EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
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
ms.translationtype: HT
ms.sourcegitcommit: 3037d92e9de377ab4b306a5a0e164e29fa6659e7
ms.openlocfilehash: 600cd62e7843274b52da5ac7200b5168311cab07
ms.contentlocale: es-es
ms.lasthandoff: 08/07/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>Configuración de la convención de codificación de .NET para EditorConfig
Las convenciones de codificación de .NET se configuran con un archivo [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Los archivos EditorConfig permiten **habilitar o deshabilitar las convenciones de codificación** y **configurar el grado en el que desea que se aplique la convención** (mediante un nivel de gravedad). Para más información acerca de cómo usar EditorConfig para aplicar la coherencia en el código base, consulte [este artículo](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options).

Hay tres categorías de convención de codificación de .NET admitidas:
- Las **[convenciones de lenguaje](#language)** son reglas relacionadas con el lenguaje C# o Visual Basic; por ejemplo, el tipo `var`/explicit, que usa un miembro con forma de expresión.
- Las **[reglas de formato](#formatting)** son reglas relacionadas con el diseño y la estructura del código para que resulte más fácil de leer; por ejemplo, llaves Allman, espacios en los bloques de control.
- Las **[convenciones de nomenclatura](#naming)** son reglas que respetan cómo se denominan los objetos; por ejemplo, los métodos `async` deben terminar en "Async". 

# <a name="language">Convenciones de lenguaje</a>
## <a name="overview"></a>Información general
**Formato de regla:**
`options_name = false|true : none|suggestion|warning|error`

Para la opción de estilo de código, debe especificar **true** (opción preferida) o **false** (opción no preferida), dos puntos (`:`) y una gravedad (`none`, `silent`, `suggestion`, `warning` o `error`). La gravedad hace referencia al nivel de cumplimiento de ese estilo que quiere en su código base.

`none` y `silent` son sinónimos y significan que no se debe mostrar indicación alguna de ningún tipo al usuario. Esto tiene el efecto de deshabilitar esta regla.

Gravedad | Efecto
------------ | -------------
none/silent | No muestra nada al usuario cuando este estilo no se sigue, pero las características de generación de código se generarán en este estilo. 
suggestion | Cuando este estilo no se sigue, se muestra al usuario como una sugerencia (puntos subyacentes en los dos primeros caracteres).
warning | Cuando este estilo no se sigue, se muestra una advertencia del compilador.
error | Cuando este estilo no se sigue, se muestra un error del compilador.

## <a name="net-language-convention-options"></a>Opciones de convención de lenguaje de .NET

- **[Configuración del estilo de código de .NET](#this_and_me)**
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
- **[Configuración del estilo de código CSharp](#csharp_codestyle)**
    - ["var"](#var)
        - ["var" para tipos integrados](#var_built_in)
        - ["var" cuando el tipo es aparente](#var_apparent)
        - ["var" en otro sitio](#var_elsewhere)
    - [Miembros con forma de expresión](#expression_body)
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
    - [Preferencias de nivel de expresión](#expression_level_csharp) -[Simplificar expresiones `default`](#expression_level_default)
    - [Preferencias de la comprobación de "NULL"](#null_checking)
        - [Expresiones Throw](#null_checking_throw_expressions)
        - [Llamadas de delegado condicionales](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">Cualificación "This." y "Me."</a>
### <a name="this_and_me_fields">Campos (IDE0003/IDE0009)</a>
|  Nombre de la opción | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todos los campos no estáticos que se han usado en métodos no estáticos comiencen por `this.` en C# o por `Me.` en Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | Prefiere que todos los campos no estáticos que se han usado en métodos no estáticos no comiencen por `this.` en C# ni por `Me.` en Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Propiedades (IDE0003/IDE0009)</a>

|  Nombre de la opción | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todas las propiedades no estáticas que se han usado en métodos no estáticos comiencen por `this.` en C# o por `Me.` en Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | Prefiere que todas las propiedades no estáticas que se han usado en métodos no estáticos *no* comiencen por `this.` en C# ni por `Me.` en Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">Métodos (IDE0003/IDE0009)</a>
|  Nombre de la opción | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todos los métodos no estáticos que se han llamado desde métodos no estáticos comiencen por `this.` en C# y por `Me.` en VB.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | Prefiere que todos los métodos no estáticos que se han llamado desde métodos no estáticos *no* comiencen por `this.` en C# ni por `Me.` en VB. | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Eventos (IDE0003/IDE0009)</a>
|  Nombre de la opción | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que todos los eventos no estáticos a los que se hace referencia desde métodos no estáticos comiencen por `this.` en C# y por `Me.` en VB.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | Prefiere que todos los eventos no estáticos a los que se hace referencia desde métodos no estáticos *no* comiencen por `this.` en C# ni por `Me.` en VB. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Palabras clave del lenguaje (int, string, etc.) frente a nombres de tipos de marco para referencias de tipo </a>
### <a name="language_keywords_variables">Variables locales, parámetros y miembros (IDE0012/IDE0014)</a>
|  Nombre de la opción | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Para variables locales, parámetros y miembros de tipo, prefiere tipos que tengan una palabra clave del lenguaje para representarlos (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar la palabra clave en lugar del nombre de tipo (`Int32`, `Int64`, etc.).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Para variables locales, parámetros y miembros de tipo, prefiere tipos que tengan una palabra clave del lenguaje para representarlos (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar el nombre de tipo (`Int32`, `Int64`, etc.) en lugar de la palabra clave.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Expresiones de acceso a miembros (IDE0013/IDE0015)</a>
|  Nombre de la opción | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere la palabra clave siempre que una expresión de acceso a miembros se use en un tipo con una representación de palabra clave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | Prefiere el nombre de tipo siempre que una expresión de acceso a miembros se use en un tipo con una representación de palabra clave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Preferencias de nivel de expresión</a>
### <a name="expression_level_object_initializers">Inicializadores de objeto (IDE0017)</a>
|  Nombre de la opción | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere que los objetos se inicialicen con inicializadores de objeto siempre que sea posible.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | Prefiere que los objetos *no* se inicialicen con inicializadores de objeto. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Inicializadores de colección (IDE0028)</a>
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

### <a name="expression_level_tuple_names">Nombres de tupla explícitos (IDE0033)</a>
|  Nombre de la opción | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+ y Visual Basic 15+

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

### <a name="expression_level_null_checking">Expresiones de fusión en la comprobación de "null" (IDE0029)</a>
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

### <a name="expression_level_null_propogation">Propagación de tipo Null en la comprobación de "null" (IDE0031)</a>
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

# <a name="csharp_codestyle">Configuración del estilo de código CSharp</a>
## <a name="var">"var" y tipos explícitos</a>
### <a name="var_built_in">"var" para tipos integrados (IDE0007, IDE0008)</a>
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

### <a name="var_apparent">"var" cuando el tipo es aparente (IDE0007, IDE0008)</a>
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

### <a name="var_elsewhere">"var" en cualquier otra parte (IDE0007, IDE0008) </a>
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

##<a name="expression_bodied_members">Miembros con forma de expresión</a>
### <a name="expression_bodied_members_methods">Métodos (IDE0022)</a>
|  Nombre de la opción | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 6.0+

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

### <a name="expression_bodied_members_constructors">Constructores (IDE0021)</a>
|  Nombre de la opción | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 6.0+

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

### <a name="expression_bodied_members_operators">Operadores (IDE0023, IDE0024)</a>
|  Nombre de la opción | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 6.0+

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

### <a name="expression_bodied_members_properties">Propiedades (IDE0025)</a>
|  Nombre de la opción | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+

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

### <a name="expression_bodied_members_indexers">Indexadores (IDE0026)</a>
|  Nombre de la opción | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+

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

### <a name="expression_bodied_members_accessors">Descriptores de acceso (IDE0027)</a>
|  Nombre de la opción | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+

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

## <a name="pattern_matching">Coincidencia de patrones</a>
### <a name="pattern_matching_is_cast">"is" con comprobación de "conversión" (IDE0020)</a>
|  Nombre de la opción | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+

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

### <a name="pattern_matching_as_null">"as" con la comprobación "null" (IDE0019)</a>
|  Nombre de la opción | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+

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

### <a name="inlined_variable_declarations">Declaraciones de variables insertadas (IDE0018)</a>
|  Nombre de la opción | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere variables `out` que se declaren como inline siempre que sea posible. | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | Prefiere variables `out` que se declaren explícitamente.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">Preferencias de nivel de expresión</a>
### <a name="expression_level_default">Simplifica expresiones `default` (IDE0034) </a>
|  Nombre de la opción | `csharp_prefer_simple_default_expression` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.1+ y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Prefiere `default` sobre `default(T)` | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | Prefer. | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">Preferencias de la comprobación de "NULL"</a>
### <a name="null_checking_throw_expressions">Expresiones Throw (IDE0016)</a>
|  Nombre de la opción | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# 7.0+

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

### <a name="null_checking_conditional_delegate_calls">Prefiere llamadas de delegado condicionales (IDE0041)</a>
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

# <a name="formatting">Reglas de formato</a>
## <a name="overview"></a>Información general
**Formato de regla:**
`options_name = false|true`

En las opciones de formato debe especificar **true** (opción preferida) o **false** (opción no preferida) excepto en un par de los casos en los que debe especificar las condiciones que desea aplicar a la regla.

## <a name="net-formatting-options"></a>Opciones de formato de .NET

- **[Configuración de formato de .NET](#usings)**
    - [Organización de instrucciones Using](#usings)
        - [Ordenar primero las directivas del sistema](#usings_sort_system_first)
- **[Configuración de formato de C#](#newline)**
    - [Opciones de nueva línea](#newline)
        - [Nueva línea antes de la llave de apertura (`{`)](#newline_before_brace)
        - [Nueva línea antes de `else`](#newline_before_else)
        - [Nueva línea antes de `catch`](#newline_before_catch)
        - [Nueva línea antes de `finally`](#newline_before_finally)
        - [Nueva línea antes de los miembros en inicializadores de objeto](#newline_before_object)
        - [Nueva línea antes de los miembros en tipos anónimos](#newline_before_anonymous)
        - [Nueva línea antes de los miembros en las cláusulas de expresión de consulta](#newline_before_query)
    - [Opciones de sangría](#indent)
        - [Aplicar sangría al contenido del caso `switch`](#indent_switch)
        - [Posición de la etiqueta](#label)
    - [Opciones de espaciado](#spacing)
        - [Espacio después de la conversión de tipos](#space_after_cast)
        - [Espacio después de las palabras clave en instrucciones de flujo de control](#space_control_flow)
        - [Espacio entre los paréntesis de lista de parámetros de declaración de método](#space_parameter_list)
        - [Espacio dentro de paréntesis en la lista de argumentos de llamada de método](#space_method_call)
        - [Espacio dentro de paréntesis en otras opciones](#space_other)
    - [Opciones de ajuste](#wrapping)
        - [Dejar instrucciones y declaraciones de miembros en la misma línea](#wrapping_statement)
        - [Dejar el bloque en una sola línea](#wrapping_block)

## <a name="usings">Organización de instrucciones Using</a>
### <a name="usings_sort_system_first">Ordenar primero las directivas del sistema</a>
|  Nombre de la opción | `dotnet_sort_system_directives_first` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C# y Visual Basic

| Valor | Descripción | Aplicado 
| ------------- |:-------------|:-------------|
| True | Las instrucciones using de System.* se ordenan alfabéticamente y se colocan antes de cualquier otra instrucción using.| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | Sin requisitos sobre el orden de las instrucciones using | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">Configuración de formato de C#</a>
## <a name="newline">Opciones de nueva línea</a>
### <a name="newline_before_brace">Nueva línea antes de la llave de apertura (`{`)</a>
|  Nombre de la opción | `csharp_new_line_before_open_brace` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| descriptores de acceso, métodos_anónimos, tipos_anónimos, bloques_control, eventos, indexadores, lambdas, funciones_locales, métodos, colección_objetos, propiedades, tipos. (Si hay varios, sepárelos por comas ','). | Se requiere que las llaves estén en una nueva línea para expresiones especificadas (estilo Allman) |
| todo | Se requiere que las llaves estén en una nueva línea para todas las expresiones (estilo Allman) |
| ninguna | Se requiere que las llaves estén en una nueva línea para todas las expresiones (K&R) |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> Nueva línea antes de `else`</a>
|  Nombre de la opción | `csharp_new_line_before_else` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Las instrucciones `else` se colocan en una nueva línea.  |
| False | Las instrucciones `else` se colocan en la misma línea.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> Nueva línea antes de `catch`</a>
|  Nombre de la opción | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Las instrucciones `catch` se colocan en una nueva línea.  |
| False | Las instrucciones `catch` se colocan en la misma línea. |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> Nueva línea antes de `finally`</a>
|  Nombre de la opción | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Se requiere que las instrucciones `finally` estén en una nueva línea después de la llave de cierre.  |
| False | Se requiere que las instrucciones `finally` estén en la misma línea que la llave de cierre.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> Nueva línea antes de los miembros en inicializadores de objeto</a>
|  Nombre de la opción | `csharp_new_line_before_members_in_object_initializers` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Se requiere que los miembros de inicializadores de objeto estén en líneas independientes.  |
| False | Se requiere que los miembros de inicializadores de objeto estén en la misma línea.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> Nueva línea antes de los miembros en tipos anónimos</a>
|  Nombre de la opción | `csharp_new_line_before_members_in_anonymous_types` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Se requiere que los miembros de tipos anónimos estén en líneas independientes.  |
| False | Se requiere que los miembros de tipos anónimos estén en la misma línea.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query">Nueva línea antes que los miembros en las cláusulas de expresión de consulta</a>
|  Nombre de la opción | `csharp_new_line_within_query_expression_clauses` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Se requiere que los elementos de las cláusulas de la expresión de consulta estén en líneas independientes.  |
| False | Se requiere que los elementos de las cláusulas de la expresión de consulta estén en la misma línea.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">Opciones de sangría</a>
### <a name="indent_switch">Aplicar sangría al contenido del caso `switch`</a>
|  Nombre de la opción | `csharp_indent_case_contents` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| True | Aplicar sangría al contenido del caso `switch`  |
| False | No aplicar sangría al contenido del caso `switch` |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="label">Posición de la etiqueta</a>
|  Nombre de la opción | `csharp_indent_labels` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción 
| ------------- |:-------------|
| one_less | Las etiquetas se colocan una sangría menos que el contexto actual. |
| no_change | Las etiquetas se colocan en la misma sangría que el contexto actual. |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">Opciones de espaciado</a>
### <a name="space_after_cast">Espacio después de la conversión</a>
|  Nombre de la opción | `csharp_space_after_cast` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado |
| ------------- |:-------------|:-------------|
| True | Se requiere un espacio entre una conversión y el valor.  | **C#:** <br>`int y = (int) x;`
| False | No se requiere ningún espacio entre una conversión y el valor. | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow">Espacio después de las palabras clave en instrucciones de flujo de control</a>
|  Nombre de la opción | `csharp_space_after_keywords_in_control_flow_statements` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado |
| ------------- |:-------------|:-------------|
| True | Se requiere un espacio después de una palabra clave. | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | No se requiere un espacio después de una palabra clave. | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list">Espacio entre los paréntesis de lista de argumentos de declaración de método</a>
|  Nombre de la opción | `csharp_space_between_method_declaration_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado |
| ------------- |:-------------|:-------------|
| True | Se requiere un espacio después de una palabra clave. | **C#:** <br>`void Bark( int x ) { ... }`
| False | No se requiere un espacio después de una palabra clave. | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call">Espacio dentro de los paréntesis en la lista de argumentos de llamada de método</a>
|  Nombre de la opción | `csharp_space_between_method_call_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado |
| ------------- |:-------------|:-------------|
| true | Se inserta un espacio entre los paréntesis de instrucciones de flujo de control. | **C#:** <br>`MyMethod( argument );`
| false | Se inserta un espacio entre los paréntesis de expresiones. | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other">Espacio dentro de los paréntesis para otras opciones</a>
|  Nombre de la opción | `csharp_space_between_parentheses` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción | Aplicado |
| ------------- |:-------------|:-------------|
| control_flow_statements | Se inserta un espacio entre los paréntesis de instrucciones de flujo de control. | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| expresiones | Se inserta un espacio entre los paréntesis de expresiones. | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | Se inserta un espacio entre los paréntesis de las conversiones de tipos. | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">Opciones de ajuste</a>
### <a name="wrapping_statement">Dejar instrucciones y declaraciones de miembros en la misma línea</a>
|  Nombre de la opción | `csharp_preserve_single_line_statements` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción |
| ------------- |:-------------|
| True | Se dejan las instrucciones y declaraciones de miembros en la misma línea.  | 
| False | Se dejan las instrucciones y declaraciones de miembros en líneas diferentes. | 

#### <a name="applied"></a>Aplicado
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">Dejar el bloque en una sola línea</a>
|  Nombre de la opción | `csharp_preserve_single_line_blocks` |
| ------------- |:-------------:|
| **Lenguajes aplicables** | C#

| Valor | Descripción |
| ------------- |:-------------|
| True | Se deja el bloque en una sola línea. | 
| False | Se deja el bloque en líneas independientes. | 

#### <a name="applied"></a>Aplicado
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming">Convenciones de nomenclatura</a>
## <a name="overview"></a>Información general
**Formato de regla:**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>Escritura de una convención de nomenclatura
Para las convenciones de nomenclatura, debe especificar **símbolos**, un **estilo** y una **gravedad**. Las convenciones de nomenclatura deben ordenarse de la más específica a la menos específica. La primera regla encontrada que se puede aplicar será la única regla que se aplica. 

### <a name="severity"></a>Gravedad
Las siguientes son opciones válidas para la gravedad de una regla de estilo de nomenclatura `none`, `silent`, `suggestion`, `warning`, `error`.

 `none` y `silent` son sinónimos y significan que no se debe mostrar indicación alguna de ningún tipo al usuario. Esto tiene el efecto de deshabilitar esta regla.

 `suggestion` significa que el usuario verá lo siguiente en la lista de errores, y lo siguiente en el IDE. La gravedad `suggetion` permite ejecutar la regla de nomenclatura, pero no hace que la compilación se interrumpa.

Gravedad | Efecto
------------ | -------------
none/silent | No muestra nada al usuario cuando este estilo no se sigue, pero las características de generación de código se generarán en este estilo. 
suggestion | Cuando este estilo no se sigue, se muestra al usuario como una sugerencia (puntos subyacentes en los dos primeros caracteres).
warning | Cuando este estilo no se sigue, se muestra una advertencia del compilador.
error | Cuando este estilo no se sigue, se muestra un error del compilador.

### <a name="symbol-specification"></a>Especificación de símbolos
Identifique a _qué_ símbolos, _con qué_ modificadores y _a qué_ nivel de accesibilidad debería aplicarse la regla de nomenclatura.

|  Nombre de la opción | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| Símbolo | Accesibilidad | Modificadores
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols = any_async_methods

dotnet_naming_symbols.any_async_methods.applicable_kinds = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers = async
``` 

### <a name="style-specification"></a>Especificación de estilo
Identifique el estilo de nomenclatura que se va a aplicar a los símbolos.

|  Nombre de la opción | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| Estilo | Descripción |
| ------------- |:-------------:|
| Prefijo | Caracteres requeridos que deben aparecer delante del identificador. |
| Sufijo | Caracteres requeridos que deben aparecer después del identificador. |
| Separador de palabras | Separador requerido entre las palabras en el identificador. |
| Uso de mayúsculas |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 

#### <a name="example-editorconfig-file"></a>Ejemplo del archivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.style = end_in_async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization = pascal_case
``` 

### <a name="example-naming-convention"></a>Convención de nomenclatura de ejemplo
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 


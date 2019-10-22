---
title: Generación de código, compilación y convenciones de nomenclatura en Microsoft Fakes| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df937d43c196193593bcfb1244bcc9e59a3c634a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660671"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Generación de código, compilación y convenciones de nomenclatura en Microsoft Fakes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describen opciones y problemas de generación y compilación de código en Fakes y se describen las convenciones de nomenclatura de los tipos, miembros y parámetros generados por Fakes.

 **Requisitos**

- Visual Studio Enterprise

## <a name="BKMK_In_this_topic"></a> En este tema
 [Generación y compilación de código](#BKMK_Code_generation_and_compilation)

- [Configuración de generación de código de stubs](#BKMK_Configuring_code_generation_of_stubs) • [Filtrado de tipos](#BKMK_Type_filtering) • [Procesamiento con stubs de clases concretas y métodos virtuales](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [Tipos internos](#BKMK_Internal_types) • [Optimización del tiempo de compilación](#BKMK_Optimizing_build_times) • [Prevención de conflictos de nombre de ensamblado](#BKMK_Avoiding_assembly_name_clashing)

  [Convenciones de nomenclatura de Fakes](#BKMK_Fakes_naming_conventions)

- [Convenciones de nomenclatura del tipo de correcciones de compatibilidad y del tipo de stub](#BKMK_Shim_type_and_stub_type_naming_conventions) • [Convenciones de nomenclatura de la propiedad de delegado de correcciones de compatibilidad o del campo de delegado de stub](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [Convenciones de nomenclatura del tipo de parámetro](#BKMK_Parameter_type_naming_conventions) • [Reglas recursivas](#BKMK_Recursive_rules)

  [Recursos externos](#BKMK_External_resources)

- [Orientación](#BKMK_Guidance)

## <a name="BKMK_Code_generation_and_compilation"></a> Generación y compilación de código

### <a name="BKMK_Configuring_code_generation_of_stubs"></a> Configuración de generación de código de stubs
 La generación de tipos de stub se configura en un archivo XML que tiene la extensión de archivo .fakes. El marco de trabajo de Fakes se integra en el proceso de compilación mediante tareas de MSBuild personalizadas y detecta los archivos en tiempo de compilación. El generador de código de Fakes compila los tipos de stub en un ensamblado y agrega la referencia al proyecto.

 En el ejemplo siguiente se muestran los tipos de stub definidos en FileSystem.dll:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>

```

### <a name="BKMK_Type_filtering"></a> Filtrado de tipos
 Pueden establecerse filtros en el archivo .fakes para restringir los tipos que deben procesarse con stubs. Puede agregar un número ilimitado de elementos Clear, Add y Remove al elemento StubGeneration para compilar la lista de los tipos seleccionados.

 Por ejemplo, este archivo .fakes genera stubs para los tipos en los espacios de nombres System y System.IO, pero excluye cualquier tipo que contenga "Handle" en el sistema:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

 Las cadenas de filtro usan una gramática simple para definir cómo deben identificarse las coincidencias:

- De forma predeterminada, los filtros no distinguen mayúsculas de minúsculas; detectan la coincidencia de subcadenas:

     `el` coincide con "hello"

- Si se agrega `!` al final del filtro, detectará una coincidencia exacta que distingue entre mayúsculas y minúsculas:

     `el!` no coincide con "hello"

     `hello!` coincide con "hello"

- Si se agrega `*` al final del filtro, detectará una coincidencia exacta con el prefijo de la cadena:

     `el*` no coincide con "hello"

     `he*` coincide con "hello"

- Varios filtros de una lista separada por punto y coma se combinan como una disyunción:

     `el;wo` coincide con "hello" y "world"

### <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Procesamiento con stubs de clases concretas y métodos virtuales
 De forma predeterminada, se generan tipos de stub para todas las clases no selladas. Es posible restringir los tipos de stub a clases abstractas a través del archivo de configuración .fakes:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="BKMK_Internal_types"></a> Tipos internos
 El generador de código de Fakes generará tipos de correcciones de compatibilidad y tipos de stub para los tipos que son visibles para el ensamblado de Fakes generado. Para que los tipos internos de un ensamblado corregido para compatibilidad sean visibles para Fakes y para el ensamblado de prueba, agregue atributos <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> al código de ensamblado corregido para compatibilidad que da visibilidad al ensamblado de Fakes generado y al ensamblado de prueba. Por ejemplo:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Tipos internos de ensamblados con nombre seguro**

 Si el ensamblado corregido para compatibilidad tiene un nombre seguro y desea acceder a los tipos internos del ensamblado:

- El ensamblado de prueba y el ensamblado de Fakes deben tener un nombre seguro.

- Debe agregar las claves públicas de la prueba y del ensamblado de Fakes a los atributos **InternalsVisibleToAttribute** de los ensamblados corregidos para compatibilidad. A continuación se muestra el aspecto que tendrán nuestros atributos de ejemplo en el código del ensamblado corregido para compatibilidad cuando este tiene un nombre seguro:

  ```csharp
  // FileSystem\AssemblyInfo.cs
  [assembly: InternalsVisibleTo("FileSystem.Fakes",
      PublicKey=<Fakes_assembly_public_key>)]
  [assembly: InternalsVisibleTo("FileSystem.Tests",
      PublicKey=<Test_assembly_public_key>)]
  ```

  Si el ensamblado corregido para compatibilidad tiene un nombre seguro, el marco de trabajo de Fakes firmará automáticamente de forma segura el ensamblado de Fakes generado. Es necesario firmar de forma segura el ensamblado de prueba. Consulte [Crear y utilizar ensamblados con nombre seguro](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

  La plataforma de Fakes usa la misma clave para firmar todos los ensamblados generados, por lo que puede usar este fragmento de código como punto de partida para agregar el atributo **InternalsVisibleTo** para el ensamblado de Fakes al código de ensamblado corregido para compatibilidad.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 Para usar una clave pública diferente para el ensamblado de Fakes, como una clave creada para el ensamblado corregido para compatibilidad, especifique la ruta de acceso completa al archivo **.snk** que contiene la clave alternativa como valor de atributo `KeyFile` en el elemento `Fakes`\\`Compilation` del archivo **.fakes**. Por ejemplo:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>

```

 A continuación, debe usar la clave pública del archivo **.snk** alternativo como segundo parámetro del atributo InternalVisibleTo del ensamblado de Fakes en el código de ensamblado corregido para compatibilidad:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

 En el ejemplo anterior, los valores `Alternate_public_key` y `Test_assembly_public_key` puede ser iguales.

### <a name="BKMK_Optimizing_build_times"></a> Optimización del tiempo de compilación
 La compilación de los ensamblados de Fakes puede aumentar considerablemente el tiempo de compilación. Puede reducir el tiempo de compilación si genera los ensamblados de Fakes para ensamblados del sistema de .NET y ensamblados de terceros en un proyecto centralizado independiente. Dado que estos ensamblados rara vez cambian en el equipo, puede volver a usar los ensamblados de Fakes generados en otros proyectos.

 En los proyectos de prueba unitaria, puede simplemente tomar una referencia a los ensamblados de Fakes compilados que se encuentran en FakesAssemblies en la carpeta del proyecto.

1. Cree una nueva biblioteca de clases con la versión en tiempo de ejecución de .NET que coincida con los proyectos de prueba. Llamémosla Fakes.Prebuild. Quite el archivo class1.cs del proyecto, ya que no es necesario.

2. Agregue una referencia a todos los ensamblados del sistema y de terceros para los que necesitará Fakes.

3. Agregue un archivo .fakes para cada ensamblado y compilación.

4. Desde el proyecto de prueba

    - Asegúrese de que tiene una referencia al archivo DLL de tiempo de ejecución de Fakes:

         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll

    - Para cada ensamblado para el que creó Fakes, agregue una referencia al archivo DLL correspondiente en la carpeta Fakes.Prebuild\FakesAssemblies del proyecto.

### <a name="BKMK_Avoiding_assembly_name_clashing"></a> Prevención de conflictos de nombre de ensamblado
 En un entorno de Team Build, todos los resultados de la compilación se combinan en un solo directorio. En el caso de varios proyectos con Fakes, podría darse que los ensamblados de Fakes de una versión diferente se reemplacen entre sí. Por ejemplo, tanto TestProject1 fakes mscorlib.dll de .NET Framework 2.0 como TestProject2 fakes mscorlib.dll para .NET Framework 4 generarían un ensamblado de Fakes mscorlib.Fakes.dll.

 Para evitar este problema, Fakes debe crear automáticamente nombres de ensamblado de Fakes cualificados para la versión para las referencias que no son del proyecto al agregar los archivos .fakes. Un nombre de ensamblado de Fakes cualificado para la versión inserta un número de versión cuando se crea el nombre del ensamblado de Fakes:

 Dado un ensamblado MyAssembly y una versión 1.2.3.4, el nombre del ensamblado de Fakes es MyAssembly.1.2.3.4.Fakes.

 Puede cambiar o quitar esta versión modificando el atributo Version del elemento Assembly en el archivo .fakes:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>

```

## <a name="BKMK_Fakes_naming_conventions"></a> Convenciones de nomenclatura de Fakes

### <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Convenciones de nomenclatura del tipo de correcciones de compatibilidad y del tipo de stub
 **Espacios de nombres**

- El sufijo .fakes se agrega al espacio de nombres.

   Por ejemplo, el espacio de nombres `System.Fakes` contiene los tipos de correcciones de compatibilidad del espacio de nombres System.

- Global.Fakes contiene el tipo de correcciones de compatibilidad del espacio de nombres vacío.

  **Nombres de tipo**

- Se agrega el prefijo Shim al nombre del tipo para generar el nombre del tipo de correcciones de compatibilidad.

   Por ejemplo, ShimExample es el tipo de correcciones de compatibilidad del tipo Example.

- Se agrega el prefijo Stub al nombre del tipo para generar el nombre del tipo de stub.

   Por ejemplo, StubIExample es el tipo de stub del tipo IExample.

  **Argumentos de tipo y estructuras de tipo anidado**

- Se copian los argumentos de tipo genérico.

- Se copia la estructura de tipo anidado para los tipos de correcciones de compatibilidad.

### <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Convenciones de nomenclatura de la propiedad de delegado de correcciones de compatibilidad o del campo de delegado de stub
 **Reglas básicas** de la nomenclatura de campo, a partir de un nombre vacío:

- Se anexa el nombre del método.

- Si el nombre del método es una implementación de interfaz explícita, se quitan los puntos.

- Si el método es genérico, se anexa `Of`*n*, donde *n* es el número de argumentos de método genérico.

  Los **nombres de métodos especiales**, como los captadores o establecedores de propiedad, se tratan tal como se describe en la tabla siguiente.

|Si el método es...|Ejemplo|Nombre de método anexado|
|-------------------|-------------|--------------------------|
|Un **constructor**|`.ctor`|`Constructor`|
|Un **constructor** estático|`.cctor`|`StaticConstructor`|
|Un **descriptor de acceso** con el nombre de método compuesto por dos partes separadas por "_" (por ejemplo, captadores de propiedades)|*kind_name* (caso común, pero no impuesto por ECMA)|*NameKind*, donde ambas partes se pusieron en mayúscula y se intercambiaron|
||Captador de propiedad `Prop`|`PropGet`|
||Establecedor de propiedad `Prop`|`PropSet`|
||Agregador de evento|`Add`|
||Eliminador de evento|`Remove`|
|Un **operador** compuesto por dos partes|`op_name`|`NameOp`|
|Por ejemplo: operador +|`op_Add`|`AddOp`|
|Para un **operador de conversión**, se anexa el tipo de valor devuelto.|`T op_Implicit`|`ImplicitOpT`|

 **Notas**

- Los **captadores y establecedores de indizadores** se tratan de forma similar a la propiedad. El nombre predeterminado de un indizador es `Item`.

- Los nombres del **parámetro de tipo** se transforman y se concatenan.

- El **tipo de valor devuelto** se omite a menos que haya una ambigüedad de sobrecarga. Si este es el caso, el tipo de valor devuelto se anexa al final del nombre.

### <a name="BKMK_Parameter_type_naming_conventions"></a> Convenciones de nomenclatura del tipo de parámetro

|Dado...|La cadena anexada es...|
|-----------|-------------------------|
|Un **tipo**`T`|T<br /><br /> Se quitan el espacio de nombres, la estructura anidada y las marcas genéricas.|
|Un **parámetro de salida**`out T`|`TOut`|
|Un **parámetro de referencia**`ref T`|`TRef`|
|Un **tipo de matriz**`T[]`|`TArray`|
|Un tipo de **matriz multidimensional**`T[ , , ]`|`T3`|
|Un tipo de **puntero**`T*`|`TPtr`|
|Un **tipo genérico**`T<R1, …>`|`TOfR1`|
|Un **argumento de tipo genérico**`!i` del tipo`C<TType>`|`Ti`|
|Un **argumento de método genérico**`!!i` del método`M<MMethod>`|`Mi`|
|Un **tipo anidado**`N.T`|Se anexa `N` y después `T`.|

### <a name="BKMK_Recursive_rules"></a> Reglas recursivas
 Las siguientes reglas se aplican de forma recursiva:

- Dado que Fakes usa C# para generar sus ensamblados, se aplica la secuencia de escape "_" (subrayado) a cualquier carácter que pueda generar un token de C# no válido.

- Si un nombre resultante entra en conflicto con algún miembro del tipo declarativo, se usa un esquema de numeración anexando un contador de dos dígitos que empieza en 01.

## <a name="BKMK_External_resources"></a> Recursos externos

### <a name="BKMK_Guidance"></a> Orientación
 [Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Otras referencias
 [Aislar el código en pruebas con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)

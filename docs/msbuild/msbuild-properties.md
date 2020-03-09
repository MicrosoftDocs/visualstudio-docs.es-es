---
title: Propiedades de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39f1f612244fedcc707475d067e67500dc76e1d9
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633296"
---
# <a name="msbuild-properties"></a>propiedades de MSBuild

Las propiedades son pares nombre-valor que se pueden utilizar para configurar compilaciones. Las propiedades son útiles para pasar valores a tareas, evaluar condiciones y almacenar valores a los que se hará referencia en el archivo del proyecto.

## <a name="define-and-reference-properties-in-a-project-file"></a>Definir y hacer referencia a propiedades en un archivo de proyecto

 Las propiedades se declaran mediante la creación de un elemento que tenga el nombre de la propiedad como elemento secundario de un elemento [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Por ejemplo, el código XML siguiente crea una propiedad denominada `BuildDir` cuyo valor es `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 En el archivo de proyecto, se hace referencia a las propiedades mediante la sintaxis $(\<NombreDePropiedad>). En el ejemplo anterior, se usa $(BuildDir) para hacer referencia a la propiedad.

 Los valores de propiedad se pueden cambiar si se vuelve a definir la propiedad. Se puede asignar un nuevo valor a la propiedad `BuildDir` mediante este código XML:

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 Las propiedades se evalúan en el orden en que aparecen en el archivo del proyecto. El nuevo valor de `BuildDir` debe declararse después de que se haya asignado el valor anterior.

## <a name="reserved-properties"></a>Propiedades reservadas

 MSBuild reserva algunos nombres de propiedades para almacenar información sobre el archivo del proyecto y los archivos binarios de MSBuild. Como a cualquier otra propiedad, a estas propiedades se hace referencia mediante la notación $. Por ejemplo, $(MSBuildProjectFile) devuelve el nombre de archivo completo del proyecto, incluida la extensión.

 Para obtener más información, vea [Cómo: Hacer referencia al nombre o la ubicación del archivo del proyecto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) y [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="environment-properties"></a>Propiedades de entorno

 En los archivos de proyecto, se puede hacer referencia a las variables de entorno de la misma manera que en el caso de las propiedades reservadas. Por ejemplo, para utilizar la variable de entorno `PATH` en el archivo de proyecto, utilice $(Path). Si el proyecto incluye la definición de una propiedad que tiene el mismo nombre que una propiedad de entorno, la propiedad del proyecto reemplaza el valor de la propiedad de entorno.

 Cada proyecto de MSBuild tiene un bloque de entorno aislado: solo ve las lecturas y escrituras de su propio bloque.  MSBuild solo lee las variables de entorno cuando inicializa la colección de propiedades, antes de que se evalúe o compile el archivo de proyecto. Después, las propiedades del entorno son estáticas, es decir, cada herramienta generada se inicia con los mismos nombres y valores.

 Para obtener el valor actual de las variables de entorno desde una herramienta generada, use las [Funciones de propiedad](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Sin embargo, el método preferido es usar el parámetro de tarea <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Las propiedades de entorno establecidas en esta matriz de cadenas se pueden pasar a la herramienta generada sin afectar a las variables de entorno del sistema.

> [!TIP]
> No todas las variables de entorno se leen para convertirse en propiedades iniciales. Las variables de entorno cuyo nombre no sea un nombre de propiedad de MSBuild válido, como "386", se omiten.

 Para obtener más información, vea [Cómo: Usar variables de entorno al compilar](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="registry-properties"></a>Propiedades del Registro

 Para leer los valores del Registro del sistema, use la sintaxis siguiente, donde `Hive` es el subárbol del Registro (por ejemplo, **HKEY_LOCAL_MACHINE**), `MyKey` es el nombre de clave, `MySubKey` es el nombre de subclave y `Value` es el valor de la subclave.

```xml
$(registry:Hive\MyKey\MySubKey@Value)
```

 Para obtener el valor predeterminado de la subclave, omita `Value`.

```xml
$(registry:Hive\MyKey\MySubKey)
```

 Este valor del Registro puede usarse para inicializar una propiedad de compilación. Por ejemplo, para crear una propiedad de compilación que represente la página principal del explorador web de Visual Studio, use este código:

```xml
<PropertyGroup>
  <VisualStudioWebBrowserHomePage>
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)
  </VisualStudioWebBrowserHomePage>
<PropertyGroup>
```

## <a name="global-properties"></a>Propiedades globales

 MSBuild permite establecer propiedades en la línea de comandos mediante el modificador **-property** (o **-p**). Los valores de estas propiedades globales reemplazan los valores de propiedad establecidos en el archivo del proyecto. Esto incluye las propiedades de entorno pero no las propiedades reservadas ya que estas no se pueden cambiar.

 En el siguiente ejemplo, se establece la propiedad global `Configuration` en `DEBUG`.

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 Las propiedades globales también se pueden establecer o modificar para proyectos secundarios en una compilación de varios proyectos mediante el atributo `Properties` de la tarea de MSBuild. Las propiedades globales también se reenvían a los proyectos secundarios, a menos que se use el atributo `RemoveProperties` de la tarea MSBuild para especificar la lista de propiedades que no se reenvían. Para más información, consulte [Tarea de MSBuild](../msbuild/msbuild-task.md).

 Si se especifica una propiedad mediante el atributo `TreatAsLocalProperty` en una etiqueta de proyecto, ese valor de propiedad global no reemplaza el valor de propiedad que se establece en el archivo de proyecto. Para obtener más información, vea [Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md) y [Cómo: Compilar los mismos archivos de código fuente con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md).

## <a name="property-functions"></a>Funciones de propiedad

 A partir de .NET Framework versión 4, se pueden usar funciones de propiedad para evaluar los scripts de MSBuild. Se puede leer la hora del sistema, comparar cadenas, buscar coincidencias de expresiones regulares y realizar muchas otras acciones en el script de compilación sin usar tareas de MSBuild.

 Se pueden usar métodos de tipo string (instancia) con cualquier valor de propiedad y se puede llamar a los métodos estáticos de muchas clases del sistema. Por ejemplo, se puede establecer una propiedad de compilación en la fecha de hoy de la manera siguiente:

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 Para obtener más información y una lista de las funciones de propiedad, vea [Funciones de propiedad](../msbuild/property-functions.md).

## <a name="create-properties-during-execution"></a>Crear propiedades durante la ejecución

 A las propiedades ubicadas fuera de los elementos `Target` se les asignan valores durante la fase de evaluación de una compilación. En la siguiente fase de la ejecución, se pueden crear o modificar propiedades como se indica a continuación:

- Cualquier tarea puede emitir una propiedad. Para emitir una propiedad, el elemento [Task](../msbuild/task-element-msbuild.md) debe tener un elemento [Output](../msbuild/output-element-msbuild.md) secundario que tenga un atributo `PropertyName`.

- La tarea [CreateProperty](../msbuild/createproperty-task.md) puede emitir una propiedad. (en desuso).

- A partir de .NET Framework 3.5, los elementos `Target` pueden contener elementos `PropertyGroup` que pueden contener declaraciones de propiedad.

## <a name="store-xml-in-properties"></a>Almacenar XML en propiedades

 Las propiedades pueden contener código XML arbitrario, que puede ayudar a pasar valores a las tareas o a mostrar información de registro. En el ejemplo siguiente se muestra la propiedad `ConfigTemplate`, que tiene un valor que contiene código XML y referencias a otras propiedades. MSBuild reemplaza dichas referencias con los respectivos valores de propiedad. Los valores de propiedad se asignan en el orden en que aparecen. Por consiguiente, en este ejemplo, `$(MySupportedVersion)`, `$(MyRequiredVersion)`y `$(MySafeMode)` ya deben haberse definido.

```xml
<PropertyGroup>
    <ConfigTemplate>
        <Configuration>
            <Startup>
                <SupportedRuntime
                    ImageVersion="$(MySupportedVersion)"
                    Version="$(MySupportedVersion)"/>
                <RequiredRuntime
                    ImageVersion="$(MyRequiredVersion)"
                    Version="$(MyRequiredVersion)"
                    SafeMode="$(MySafeMode)"/>
            </Startup>
        </Configuration>
    </ConfigTemplate>
</PropertyGroup>
```

## <a name="see-also"></a>Vea también

- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Cómo: Usar variables de entorno en una compilación](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [Cómo: Hacer referencia al nombre o la ubicación del archivo de proyecto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [Cómo: Compilar los mismos archivos de código fuente con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)

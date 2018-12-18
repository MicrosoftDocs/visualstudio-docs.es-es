---
title: MSBuild Properties1 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c839cebc63e14490f8793feffd4580798779288
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199282"
---
# <a name="msbuild-properties1"></a>MSBuild Properties1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Las propiedades son pares nombre-valor que se pueden utilizar para configurar compilaciones. Las propiedades son útiles para pasar valores a tareas, evaluar condiciones y almacenar valores a los que se hará referencia en el archivo del proyecto.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Definir y hacer referencia a propiedades en un archivo de proyecto  
 Las propiedades se declaran creando un elemento que tenga el nombre de la propiedad como elemento secundario de un elemento [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Por ejemplo, el código XML siguiente crea una propiedad denominada `BuildDir` cuyo valor es `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 En el archivo del proyecto, se hace referencia a las propiedades mediante la sintaxis $(`PropertyName`). En el ejemplo anterior, se usa $(BuildDir) para hacer referencia a la propiedad.  
  
 Los valores de propiedad se pueden cambiar si se vuelve a definir la propiedad. Se puede asignar un nuevo valor a la propiedad `BuildDir` mediante este código XML:  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Las propiedades se evalúan en el orden en que aparecen en el archivo del proyecto. El nuevo valor de `BuildDir` debe declararse después de que se haya asignado el valor anterior.  
  
## <a name="reserved-properties"></a>Propiedades reservadas  
 MSBuild reserva algunos nombres de propiedades para almacenar información sobre el archivo del proyecto y los archivos binarios de MSBuild. Como a cualquier otra propiedad, a estas propiedades se hace referencia mediante la notación $. Por ejemplo, $(MSBuildProjectFile) devuelve el nombre de archivo completo del proyecto, incluida la extensión.  
  
 Para obtener más información, consulte [Cómo: Hacer referencia al nombre o la ubicación del archivo del proyecto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) y [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Propiedades de entorno  
 En los archivos de proyecto, se puede hacer referencia a las variables de entorno de la misma manera que en el caso de las propiedades reservadas. Por ejemplo, para utilizar la variable de entorno `PATH` en el archivo de proyecto, utilice $(Path). Si el proyecto incluye la definición de una propiedad que tiene el mismo nombre que una propiedad de entorno, la propiedad del proyecto reemplaza el valor de la propiedad de entorno.  
  
 Cada proyecto de MSBuild tiene un bloque de entorno aislado: solo ve las lecturas y escrituras de su propio bloque.  MSBuild solo lee las variables de entorno cuando inicializa la colección de propiedades, antes de que se evalúe o compile el archivo de proyecto. Después, las propiedades del entorno son estáticas, es decir, cada herramienta generada se inicia con los mismos nombres y valores.  
  
 Para obtener el valor actual de las variables de entorno desde una herramienta generada, utilice las [funciones de propiedad](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Sin embargo, el método preferido es usar el parámetro de tarea <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Las propiedades de entorno establecidas en esta matriz de cadenas se pueden pasar a la herramienta generada sin afectar a las variables de entorno del sistema.  
  
> [!TIP]
>  No todas las variables de entorno se leen para convertirse en propiedades iniciales. Las variables de entorno cuyo nombre no sea un nombre de propiedad de MSBuild válido, como "386", se omiten.  
  
 Para obtener más información, consulte [Cómo: Utilizar variables de entorno en una compilación](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Propiedades del Registro  
 Para leer los valores del Registro del sistema, use la sintaxis que figura a continuación, donde `Hive` es el subárbol del Registro (por ejemplo, HKEY_LOCAL_MACHINE ), `Key` es el nombre de la clave, `SubKey` es el nombre de la subclave, y `Value` es el valor de la subclave.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Para obtener el valor predeterminado de la subclave, omita `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Este valor del Registro puede usarse para inicializar una propiedad de compilación. Por ejemplo, para crear una propiedad de compilación que represente la página principal del explorador web de Visual Studio, use este código:  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Propiedades globales  
 MSBuild permite establecer propiedades en la línea de comandos mediante el modificador **/property** (o **/p**). Los valores de estas propiedades globales reemplazan los valores de propiedad establecidos en el archivo del proyecto. Esto incluye las propiedades de entorno pero no las propiedades reservadas ya que estas no se pueden cambiar.  
  
 En el siguiente ejemplo, se establece la propiedad global `Configuration` en `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Las propiedades globales también se pueden establecer o modificar para proyectos secundarios en una compilación de varios proyectos mediante el atributo `Properties` de la tarea de MSBuild. Para obtener más información, consulte [Tarea de MSBuild](../msbuild/msbuild-task.md).  
  
 Si se especifica una propiedad mediante el atributo `TreatAsLocalProperty` en una etiqueta de proyecto, ese valor de propiedad global no reemplaza el valor de propiedad que se establece en el archivo de proyecto. Para obtener más información, consulte [Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md) y [Cómo: Compilar los mismos archivos de origen con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Funciones de propiedad  
 A partir de .NET Framework versión 4, se pueden usar funciones de propiedad para evaluar los scripts de MSBuild. Se puede leer la hora del sistema, comparar cadenas, buscar coincidencias de expresiones regulares y realizar muchas otras acciones en el script de compilación sin usar tareas de MSBuild.  
  
 Se pueden usar métodos de tipo string (instancia) con cualquier valor de propiedad y se puede llamar a los métodos estáticos de muchas clases del sistema. Por ejemplo, se puede establecer una propiedad de compilación en la fecha de hoy de la manera siguiente:  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Para obtener más información y una lista de las funciones de propiedad, consulte [Funciones de propiedad](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Crear propiedades durante la ejecución  
 A las propiedades ubicadas fuera de los elementos `Target` se les asignan valores durante la fase de evaluación de una compilación. En la siguiente fase de la ejecución, se pueden crear o modificar propiedades como se indica a continuación:  
  
-   Cualquier tarea puede emitir una propiedad. Para emitir una propiedad, el elemento [Task](../msbuild/task-element-msbuild.md) debe tener un elemento [Output](../msbuild/output-element-msbuild.md) secundario que tenga un atributo `PropertyName`.  
  
-   La tarea [CreateProperty](../msbuild/createproperty-task.md) puede emitir una propiedad. (en desuso).  
  
-   A partir de .NET Framework 3.5, los elementos `Target` pueden contener elementos `PropertyGroup` que pueden contener declaraciones de propiedad.  
  
## <a name="storing-xml-in-properties"></a>Almacenar código XML en las propiedades  
 Las propiedades pueden contener código XML arbitrario, que puede ayudar a pasar valores a las tareas o a mostrar información de registro. En el ejemplo siguiente se muestra la propiedad `ConfigTemplate`, que tiene un valor que contiene código XML y referencias a otras propiedades. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] reemplaza dichas referencias con los respectivos valores de propiedad. Los valores de propiedad se asignan en el orden en que aparecen. Por consiguiente, en este ejemplo, `$(MySupportedVersion)`, `$(MyRequiredVersion)`y `$(MySafeMode)` ya deben haberse definido.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)  
 [Cómo: Utilizar variables de entorno en una compilación](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Cómo: Hacer referencia al nombre o la ubicación del archivo del proyecto](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Cómo: Compilar los mismos archivos de origen con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)



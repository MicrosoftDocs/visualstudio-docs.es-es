---
title: Cómo hacer las extensiones de ida y vuelta
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: ff2865080b7d36f1a7c3b8a7680d867b92ec9c08
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905772"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Cómo: hacer que las extensiones sean compatibles con Visual Studio 2019/2017 y Visual Studio 2015

En este documento se explica cómo realizar un recorrido de ida y vuelta de proyectos de extensibilidad entre Visual Studio 2015 y Visual Studio 2019 o Visual Studio 2017. Después de completar esta actualización, un proyecto podrá abrir, compilar, instalar y ejecutar en Visual Studio 2015 y Visual Studio 2019 o 2017. Como referencia, algunas extensiones que pueden llevarse a cabo entre Visual Studio 2015 y Visual Studio 2019 o 2017 se pueden encontrar en los [ejemplos de extensibilidad del SDK de vs](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Si solo tiene previsto compilar en Visual Studio 2019/2017, pero quiere que el resultado de la extensión VSIX se ejecute en Visual Studio 2015 y Visual Studio 2019/2017, consulte el [documento de migración](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)de la extensión.

> [!NOTE]
> Debido a los cambios en Visual Studio entre versiones, algunas cosas que funcionaban en una versión no funcionan en otro. Asegúrese de que las características a las que está intentando obtener acceso están disponibles en ambas versiones o que la extensión tendrá resultados inesperados.

A continuación se muestra un resumen de los pasos que debe completar en este documento para realizar un recorrido de ida y vuelta por una VSIX:

1. Importe los paquetes de NuGet correctos.
2. Actualizar manifiesto de extensión:
    * Destino de la instalación
    * Requisitos previos
3. Actualizar CSProj:
    * Actualice `<MinimumVisualStudioVersion>`.
    * Agregue la propiedad `<VsixType>`.
    * Agregue la propiedad de depuración `($DevEnvDir)` 3 veces.
    * Agregue condiciones para importar los destinos y las herramientas de compilación.

4. Compilar y probar

## <a name="environment-setup"></a>Configuración del entorno

En este documento se da por supuesto que tiene lo siguiente instalado en el equipo:

* Visual Studio 2015 con el SDK de VS instalado
* Visual Studio 2019 o 2017 con la carga de trabajo de extensibilidad instalada

## <a name="recommended-approach"></a>Enfoque recomendado

Se recomienda encarecidamente iniciar esta actualización con Visual Studio 2015, en lugar de Visual Studio 2019 o 2017. La principal ventaja de desarrollar en Visual Studio 2015 es asegurarse de que no se hace referencia a ensamblados que no están disponibles en Visual Studio 2015. Si realiza el desarrollo en Visual Studio 2019 o 2017, existe un riesgo de que se pueda introducir una dependencia en un ensamblado que solo existe en Visual Studio 2019 o 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Asegúrese de que no hay ninguna referencia a project.jsen

Más adelante en este documento, se insertarán instrucciones de importación condicional en el archivo **. csproj* . Esto no funcionará si las referencias de NuGet se almacenan en *project.jsen*. Como tal, se recomienda que mueva todas las referencias de NuGet al archivo *packages.config* .
Si el proyecto contiene un *project.jsen* el archivo:

* Tome nota de las referencias en *project.jsen*.
* En el **Explorador de soluciones**, elimine el *project.jsen* el archivo del proyecto. Esto elimina el *project.jsen* el archivo y lo quita del proyecto.
* Vuelva a agregar las referencias de NuGet al proyecto:
  * Haga clic con el botón derecho en la **solución** y elija **administrar paquetes NuGet para la solución**.
  * Visual Studio crea automáticamente el archivo de *packages.config* .

> [!NOTE]
> Si el proyecto contenía paquetes EnvDTE, es posible que necesiten agregarse haciendo clic con el botón derecho en **referencias** seleccionando **Agregar referencia** y agregando la referencia adecuada. El uso de paquetes NuGet puede crear errores al intentar compilar el proyecto.

## <a name="add-appropriate-build-tools"></a>Agregar las herramientas de compilación adecuadas

Tenemos que asegurarnos de agregar herramientas de compilación que nos permitan compilar y depurar de forma adecuada. Microsoft ha creado un ensamblado para este llamado Microsoft. VisualStudio. SDK. BuildTasks.

Para compilar e implementar un VSIXv3 en Visual Studio 2015 y 2019/2017, necesitará los siguientes paquetes NuGet:

Versión | Herramientas integradas
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. SDK. BuildTasks. 14.0
Visual Studio 2019 o 2017 | Microsoft. VSSDK. BuildTool

Para ello:

* Agregue el paquete NuGet Microsoft. VisualStudio. SDK. BuildTasks. 14.0 al proyecto.
* Si el proyecto no contiene Microsoft. VSSDK. BuildTools, agréguelo.
* Asegúrese de que la versión de Microsoft. VSSDK. BuildTools es 15. x o superior.

## <a name="update-extension-manifest"></a>Actualizar manifiesto de extensión

### <a name="1-installation-targets"></a>1. destinos de instalación

Es necesario indicar a Visual Studio qué versiones se van a usar para crear un VSIX. Normalmente, estas referencias son a la versión 14,0 (Visual Studio 2015), la versión 15,0 (Visual Studio 2017) o la versión 16,0 (Visual Studio 2019). En nuestro caso, queremos crear una VSIX que vaya a instalar una extensión para ambos, por lo que necesitamos tener como destino ambas versiones. Si desea que la VSIX se compile e instale en versiones anteriores a la 14,0, esto se puede hacer estableciendo el número de versión anterior. sin embargo, ya no se admiten la versión 10,0 y anteriores.

* Abra el archivo *source. Extension. vsixmanifest* en Visual Studio.
* Abra la pestaña **destinos de instalación** .
* Cambie el **intervalo de versiones** a [14,0, 17,0). ' [' Indica a Visual Studio que incluya 14,0 y todas las versiones posteriores. ') ' Indica a Visual Studio que incluya todas las versiones hasta la versión 17,0, pero sin incluirla.
* Guarde todos los cambios y cierre todas las instancias de Visual Studio.

![Imagen de destinos de instalación](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. agregar requisitos previos al archivo *Extension. vsixmanifest*

Necesitamos el editor principal de Visual Studio como requisito previo. Abra Visual Studio y use el diseñador de manifiestos actualizado para insertar los requisitos previos.

Para hacerlo manualmente:

* Navegue al directorio del proyecto en el explorador de archivos.
* Abra el archivo *Extension. vsixmanifest* con un editor de texto.
* Agregue la siguiente etiqueta:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Guarde y cierre el archivo.

> [!NOTE]
> Es posible que tenga que editar manualmente la versión de requisitos previos para asegurarse de que es compatible con todas las versiones de Visual Studio 2019 o 2017. Esto se debe a que el diseñador insertará la versión mínima como la versión actual de Visual Studio (por ejemplo, 15.0.26208.0). Sin embargo, dado que otros usuarios pueden tener una versión anterior, querrá editarlo manualmente en 15,0.

En este momento, el archivo de manifiesto debería tener un aspecto similar al siguiente:

![Ejemplo de requisitos previos](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificar el archivo de proyecto (de proyecto. csproj)

Se recomienda encarecidamente tener una referencia a un. csproj abierto mientras realiza este paso. Puede encontrar varios ejemplos [aquí](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Seleccione cualquier ejemplo de extensibilidad, busque el archivo *. csproj* como referencia y ejecute los pasos siguientes:

* Navegue al directorio del proyecto en el **Explorador de archivos**.
* Abra el archivo de *proyecto. csproj* con un editor de texto.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. actualizar el MinimumVisualStudioVersion

* Establezca la versión mínima de Visual Studio en `$(VisualStudioVersion)` y agregue una instrucción condicional para ella. Agregue estas etiquetas si no existen. Asegúrese de que las etiquetas se establecen como se indica a continuación:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Agregue la propiedad VsixType.

* Agregue la siguiente etiqueta `<VsixType>v3</VsixType>` a un grupo de propiedades.

> [!NOTE]
> Se recomienda agregar esto debajo de la `<OutputType></OutputType>` etiqueta.

### <a name="3-add-the-debugging-properties"></a>3. agregar las propiedades de depuración

* Agregue el siguiente grupo de propiedades:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Elimine todas las instancias del siguiente ejemplo de código del archivo *. csproj* y los archivos *. csproj. User* :

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. agregar condiciones a las importaciones de herramientas de compilación

* Agregue instrucciones condicionales adicionales a las `<import>` etiquetas que tienen una referencia de Microsoft. VSSDK. BuildTools. Insertar `'$(VisualStudioVersion)' != '14.0' And` al principio de la instrucción de condición. Estas instrucciones aparecerán en el encabezado y el pie de página del archivo csproj.

Por ejemplo:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Agregue instrucciones condicionales adicionales a las `<import>` etiquetas que tengan un Microsoft. VisualStudio. SDK. BuildTasks. 14.0. Insertar `'$(VisualStudioVersion)' == '14.0' And` al principio de la instrucción de condición. Estas instrucciones aparecerán en el encabezado y el pie de página del archivo csproj.

Por ejemplo:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Agregue instrucciones condicionales adicionales a las `<Error>` etiquetas que tienen una referencia de Microsoft. VSSDK. BuildTools. Para ello, inserte `'$(VisualStudioVersion)' != '14.0' And` en la parte delantera de la instrucción de condición. Estas instrucciones aparecerán en el pie de página del archivo csproj.

Por ejemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Agregue instrucciones condicionales adicionales a las `<Error>` etiquetas que tengan un Microsoft. VisualStudio. SDK. BuildTasks. 14.0. Insertar `'$(VisualStudioVersion)' == '14.0' And` al principio de la instrucción de condición. Estas instrucciones aparecerán en el pie de página del archivo csproj.

Por ejemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Guarde el archivo csproj y ciérrelo. 
  * Tenga en cuenta que si usa más de un proyecto en la solución, establezca este proyecto como proyecto de inicio mediante "establecer como proyecto de inicio" en el menú contextual del proyecto. Esto garantiza que Visual Studio vuelva a abrir este proyecto después de descargarlo.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Prueba de las instalaciones de la extensión en Visual Studio 2015 y Visual Studio 2019 o 2017

En este momento, el proyecto debe estar listo para compilar un VSIXv3 que se pueda instalar en Visual Studio 2015 y Visual Studio 2017.

* Abra el proyecto en Visual Studio 2015.
* Compile el proyecto y confirme en la salida que un VSIX se compila correctamente.
* Navegue hasta el directorio del proyecto.
* Abra la carpeta *\bin\debug* .
* Haga doble clic en el archivo VSIX e instale su extensión en Visual Studio 2015 y Visual Studio 2019/2017.
* Asegúrese de que puede ver la extensión en **herramientas**  >  **extensiones y actualizaciones** en la sección **instalado** .
* Intente ejecutar o usar la extensión para comprobar que funciona.

![Buscar un VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Si el proyecto se bloquea con el mensaje que **abre el archivo**, fuerce el cierre de Visual Studio, vaya al directorio del proyecto, muestre las carpetas ocultas y elimine la carpeta *. vs* .
 
